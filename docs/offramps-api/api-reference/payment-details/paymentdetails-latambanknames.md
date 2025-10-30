---
description: >-
  Retrieves the valid banks that are supported by our Latam providers. The bank
  names returned in the response, should be used as the value for bank_name when
  creating a Latam payment_deatil.
hidden: true
---

# PaymentDetails#LatamBankNames

{% hint style="info" %}
"I've hidden this page for now. Because Latam support has not been tested for months. If there is integrator demand I will re-test and re-enable" - Cam
{% endhint %}

#### Example Request

```json
curl https://{{base_url}}/latam_bank_names?country_code=INSERT_COUNTRY_CODE&rails=INSERT_RAILS
-X GET \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-type: application/json" \
```

#### Endpoint Information

## Get Latam Bank Names

<mark style="color:green;">`GET`</mark> `https://{{base_url}}/latam_bank_names?country_code=INSERT_COUNTRY_CODE&rails=INSERT_RAILS`

#### Query Parameters

| Name                                            | Type   | Description                                            |
| ----------------------------------------------- | ------ | ------------------------------------------------------ |
| country\_code<mark style="color:red;">\*</mark> | String | Must be one of the following values: \[AR CO MX CL PE] |
| rails                                           | String | For CO rails must be `koywe`                           |

#### Request Body

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "bank_names": [
	"BANAMEX",
	"BBVA BANCOMER",
	"SANTANDER",
	"HSBC",
	"BAJIO",
	"INBURSA",
	"MIFEL",
	"SCOTIABANK",
	"BANREGIO",
	"BANSI",
	"BANORTE",
	"ACCENDO BANCO",
	"AMERICAN EXPRESS",
	"BANK OF AMERICA",
	"MUFG",
	"JP MORGAN",
	"BMONEX",
	"VE POR MAS",
	"DEUTSCHE",
	"CREDIT SUISSE",
	"AZTECA",
	"AUTOFIN",
	"BARCLAYS",
	"COMPARTAMOS",
	"MULTIVA BANCO",
	"ACTINVER",
	"INTERCAM BANCO",
	"BANCOPPEL",
	"ABC CAPITAL",
	"CONSUBANCO",
	"VOLKSWAGEN",
	"CIBANCO",
	"BBASE",
	"BANKAOOL",
	"PAGATODO",
	"INMOBILIARIO",
	"DONDE",
	"BANCREA",
	"ICBC",
	"SABADELL",
	"SHINHAN",
	"MIZUHO BANK",
	"BANCO S3",
	"MONEXCB",
	"GBM",
	"MASARI",
	"VALUE",
	"ESTRUCTURADORES",
	"VECTOR",
	"MULTIVA CBOLSA",
	"FINAMEX",
	"VALMEX",
	"PROFUTURO",
	"CB INTERCAM",
	"CI BOLSA",
	"FINCOMUN",
	"HDI SEGUROS",
	"REFORMA",
	"STP",
	"EVERCORE",
	"CREDICAPITAL",
	"KUSPIT",
	"UNAGRA",
	"ASP INTEGRA OPC",
	"LIBERTAD",
	"CAJA POP MEXICA",
	"CRISTOBAL COLON",
	"CAJA TELEFONIST",
	"FONDO (FIRA)",
	"INVERCAP",
	"FOMPED",
	"SANTANDER2",
	"CLS",
	"INDEVAL",
	"BBVA BANCOMER2",
	"HSBC2",
	"ZURICH",
	"ARCUS",
	"NU MEXICO",
	"BABIEN",
	"BANOBRAS - Updated Name ",
	"BANCOMEXT - Updated",
	"BANJERCITO",
	"Nvio Pagos México",
	"BANCO COVALTO",
	"OPM",
	"AFIRME",
	"INVEX ",
	"HIPOTECARIA FED"
]
}
```
{% endtab %}
{% endtabs %}
