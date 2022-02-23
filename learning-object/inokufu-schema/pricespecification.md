# PriceSpecification

"@context": "https://schema.org/"

"@type": "PriceSpecification"

### Price

Value of the price (float). If the LO is free, price MIUST be 0.0

### Price currency

Standard 3 letters code according to ISO 4217: EUR for euros USD for US dollars GBP for UK pounds etc. See here for the full list: https://en.wikipedia.org/wiki/ISO\_4217&#x20;

### Price free

Boolean value which indicates if the LO is free. If the LO can be accessed for free it MUST be true If the LO can only be accessed by paying, it MUST be false. If the LO can be both accessed for free and by paying (for example MOOC on Coursera, with and without the final certificate), it MUST be true.
