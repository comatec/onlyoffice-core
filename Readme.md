
[![License](https://img.shields.io/badge/License-GNU%20AGPL%20V3-green.svg?style=flat)](https://www.gnu.org/licenses/agpl-3.0.en.html)     ![x2tconverter](https://img.shields.io/badge/x2tconverter-v2.0.2.376-blue.svg?style=flat) ![Platforms Windows | OS X | Linux](https://img.shields.io/badge/Platforms-Windows%20%7C%20OS%20X%20%7C%20Linux%20-lightgray.svg?style=flat)

## Problem fixed

Repeatedly saving an edited PDF could cause cumulative file-size growth due to
incremental xref updates and re-embedded image and font resources.

The fix rewrites the PDF instead of appending incremental updates and
deduplicates reusable **identical** image and font streams (CRC of stream
bytes). Page content streams and Form XObjects are excluded from deduplication
to preserve visible content.

**Do not** merge Image XObjects by Width×Height alone — distinct charts in
exam PDFs often share dimensions and were incorrectly collapsed (missing /
swapped graphics after save). That size-only pass was disabled.

## Core
Server core components which are a part of [ONLYOFFICE Document Server][2] and [ONLYOFFICE Desktop Editors][4]. Enable the conversion between the most popular office document formats: DOC, DOCX, ODT, RTF, TXT, PDF, HTML, EPUB, XPS, DjVu, XLS, XLSX, ODS, CSV, PPT, PPTX, ODP.

## Project Information

Official website: [http://www.onlyoffice.com](http://onlyoffice.com "http://www.onlyoffice.com")

Code repository: [https://github.com/ONLYOFFICE/core](https://github.com/ONLYOFFICE/core "https://github.com/ONLYOFFICE/core")

SaaS version: [https://www.onlyoffice.com/cloud-office.aspx](https://www.onlyoffice.com/cloud-office.aspx "https://www.onlyoffice.com/cloud-office.aspx")

## User Feedback and Support

If you have any problems with or questions about [ONLYOFFICE Document Server][2], please visit our official forum to find answers to your questions: [forum.onlyoffice.com][1] or you can ask and answer ONLYOFFICE development questions on [Stack Overflow][3].

  [1]: https://forum.onlyoffice.com
  [2]: https://github.com/ONLYOFFICE/DocumentServer
  [3]: http://stackoverflow.com/questions/tagged/onlyoffice
  [4]: https://github.com/ONLYOFFICE/DesktopEditors
  
## License

Core is released under an GNU AGPL v3.0 license. See the LICENSE file for more information.
