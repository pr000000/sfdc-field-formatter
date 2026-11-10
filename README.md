# SFDC Field Formatter

A browser-based tool I built during my AWS internship to speed up Salesforce lead lookup. It reads Excel exports from Chinese business-registry platforms (Qichacha / Aiqicha) and turns them into Salesforce fields that can be copied and pasted directly into a search.

## Features

- **Automatic header detection:** Qichacha exports put a disclaimer row above the real column headers. The tool skips it and finds the header row on its own.
- **Field mapping:** Columns are mapped to the Salesforce fields used for lookup:

  | Salesforce field | Source column |
  |---|---|
  | Account name | 英文名 (English name) |
  | Account also known as | 系统匹配企业名称 / 企业名称 (company name) |
  | Registration number | 统一社会信用代码 / USCC |
  | Website | 官网Domain / 官网 / 网址 |
  | Total addressable spending | 注册资本 (registered capital) |

- **Domain cleaning:** Removes the protocol, `www` and TLD suffixes, so only the core domain is left for matching.
- **Length handling:** Any field longer than 1,200 characters is split into segments at commas, so each segment fits the Salesforce search limit.
- **Flexible input:** Only fields whose source columns exist in the file are shown.
- **One-click copy:** Each text block has its own copy button.

## How to Use

1. Download `index.html` and open it in Chrome, Edge or Firefox.
2. Click the upload area or drag an `.xlsx` file into it.
3. Copy each field and paste it into the Salesforce search.

No installation is needed. All processing runs locally in the browser, and no data is uploaded.

## Tech Stack

- HTML, CSS, JavaScript
- [SheetJS (xlsx-js-style)](https://github.com/gitbrent/xlsx-js-style) for reading Excel files
- Font Awesome for icons

## Sample Data

`sample_data.xlsx` contains synthetic company records for demonstration only. This repository does not include any real company, customer or internal data.

## Author

Peiran (Cynthia) Jing
