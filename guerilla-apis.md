# Guerrilla APIs

_Speaker: Russell Keith-Magee_


Most places to get info don't have APIs, but they are on the internet. Which
means the data is still accessible.

## Retrieving Data

### RSS

If they publish RSS, then you can parse it with feedparser. Set up background
tasks to grab the content on a schedule, but pay attention to server failures
and object IDs (which are in practice not unique, and not really IDs). Pay
attention to RSS update frequency and don't hammer the service.

### Email

If you can get the data via email, you can use something like Mailgun which
has a REST API to incoming mail. The content of the email can vary wildly, and
most often what you really want is the attachment. Look out for the
"message/rfc822" which says the email contains another email.

Email has a MIME type, and each attachment will contain a MIME type, unless
the email is sent by Outlook, which sends all attachments as binary data. You
can use mimetypes.guess\_type(), but it's not fool-proof.

You can parse DOCX files with python-docx, and convert DOC files to PDFs
with OpenOffice (which has command-line tools).

### PDFs

PDF is a printing format, which includes vector-based drawing instructions and
may contain attachments as well. There is almost always a predictable structure
in PDFs because people use similar tools to create them, as opposed to creating
them by hand. You can use PDF2HTML and then parse the resulting HTML, but it's
not very often successful. There another library called PDFMiner, which is
available on PyPI, but is not actively maintained -- but since the PDF format
is stable that's not too concerning.

See slides for examples on how to use PDFMiner.


## Submitting Data

To submit forms that rely heavily on Javascript, use Selenium.

