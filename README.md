# AraibcPdfUnicodeGlyphsResharper
this can be use with itext7 and also with PdfSharp
the following example show how to use with PsdSharp. MigraDoc

```
using PdfSharp.Drawing;
using PdfSharp.Pdf;
using AraibcPdfUnicodeGlyphsResharper;
namespace MigraDocArabic
{
internal class PrintArabicUsingPdfSharp
{
    public PrintArabicUsingPdfSharp(string path)
    {
        PdfDocument document = new PdfDocument();
        document.Info.Title = "Created with PDFsharp";
        System.Text.Encoding.RegisterProvider(System.Text.CodePagesEncodingProvider.Instance);
        // Create an empty page
        PdfPage page = document.AddPage();

        // Get an XGraphics object for drawing
        XGraphics gfx = XGraphics.FromPdfPage(page);

        // Create a font
        XFont font = new XFont("Arial", 20, XFontStyle.BoldItalic);
        var xArabicString = "كتابة اللغة  العربية شيئ جميل".ArabicWithFontGlyphsToPfd();
        // Draw the text
        gfx.DrawString("Hello, World!", font, XBrushes.Black, new XRect(0, 0, page.Width, page.Height), XStringFormats.Center);
        gfx.DrawString(xArabicString, font, XBrushes.Black, new XRect(50, 50, page.Width, page.Height), XStringFormats.Center);

        // Save the document...
        document.Save(path);

    }
}
```
