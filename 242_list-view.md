# Blazorise List View component

List views are a flexible and powerful component for displaying a series of content in a contained scrollable view by providing a data source.

📊 The Community License has a limitation of 1000 items. Unlock full access to all features with
    
        our premium plans.

List views use ListGroup behind the covers, so you may make use of the ListGroup underlying APIs.

## Examples

### Basic

- Antarctica
- United Arab Emirates
- Afghanistan
- Albania
- Armenia
- Curacao
- Sint Maarten
- Netherlands Antilles
- Angola
- Argentina
- Australia
- Cocos Islands
- Christmas Island
- Heard Island and McDonald Islands
- Kiribati
- Norfolk Island
- Nauru
- Tuvalu
- Aruba
- Azerbaijan
- Bosnia and Herzegovina
- Barbados
- Bangladesh
- Bulgaria
- Bahrain
- Burundi
- Bermuda
- Brunei
- Bolivia
- Brazil
- Bahamas
- Bhutan
- Botswana
- Belarus
- Belize
- Canada
- Democratic Republic of the Congo
- Switzerland
- Liechtenstein
- Chile
- China
- Colombia
- Costa Rica
- Cuba
- Cape Verde
- Czech Republic
- Djibouti
- Denmark
- Faroe Islands
- Greenland
- Dominican Republic
- Algeria
- Egypt
- Eritrea
- Ethiopia
- Andorra
- Austria
- Aland Islands
- Belgium
- Saint Barthelemy
- Cyprus
- Germany
- Estonia
- Spain
- Finland
- France
- French Guiana
- Guadeloupe
- Greece
- Ireland
- Italy
- Kosovo
- Luxembourg
- Monaco
- Montenegro
- Saint Martin
- Martinique
- Malta
- Netherlands
- Saint Pierre and Miquelon
- Portugal
- Reunion
- Slovenia
- Slovakia
- San Marino
- French Southern Territories
- Vatican
- Mayotte
- Fiji
- Falkland Islands
- United Kingdom
- Guernsey
- South Georgia and the South Sandwich Islands
- Isle of Man
- Jersey
- Georgia
- Ghana
- Gibraltar
- Gambia
- Guinea
- Guatemala
- Guyana
- Hong Kong
- Honduras
- Croatia
- Haiti
- Hungary
- Indonesia
- Israel
- Palestinian Territory
- India
- Iraq
- Iran
- Iceland
- Jamaica
- Jordan
- Japan
- Kenya
- Kyrgyzstan
- Cambodia
- Comoros
- North Korea
- South Korea
- Kuwait
- Cayman Islands
- Kazakhstan
- Laos
- Lebanon
- Sri Lanka
- Liberia
- Lesotho
- Lithuania
- Latvia
- Libya
- Western Sahara
- Morocco
- Moldova
- Madagascar
- Macedonia
- Myanmar
- Mongolia
- Macao
- Mauritania
- Mauritius
- Maldives
- Malawi
- Mexico
- Malaysia
- Mozambique
- Namibia
- Nigeria
- Nicaragua
- Bouvet Island
- Norway
- Svalbard and Jan Mayen
- Nepal
- Cook Islands
- Niue
- New Zealand
- Pitcairn
- Tokelau
- Oman
- Panama
- Peru
- Papua New Guinea
- Philippines
- Pakistan
- Poland
- Paraguay
- Qatar
- Romania
- Serbia
- Serbia and Montenegro
- Russia
- Rwanda
- Saudi Arabia
- Solomon Islands
- Seychelles
- Sudan
- Sweden
- Singapore
- Saint Helena
- Sierra Leone
- Somalia
- Suriname
- South Sudan
- Sao Tome and Principe
- Syria
- Swaziland
- Thailand
- Tajikistan
- Turkmenistan
- Tunisia
- Tonga
- Turkey
- Trinidad and Tobago
- Taiwan
- Tanzania
- Ukraine
- Uganda
- American Samoa
- Bonaire, Saint Eustatius and Saba
- Ecuador
- Micronesia
- Guam
- British Indian Ocean Territory
- Marshall Islands
- Northern Mariana Islands
- Puerto Rico
- Palau
- El Salvador
- Turks and Caicos Islands
- East Timor
- United States Minor Outlying Islands
- United States
- British Virgin Islands
- U.S. Virgin Islands
- Uruguay
- Uzbekistan
- Venezuela
- Vietnam
- Vanuatu
- Samoa
- Central African Republic
- Republic of the Congo
- Cameroon
- Gabon
- Equatorial Guinea
- Chad
- Antigua and Barbuda
- Anguilla
- Dominica
- Grenada
- Saint Kitts and Nevis
- Saint Lucia
- Montserrat
- Saint Vincent and the Grenadines
- Burkina Faso
- Benin
- Ivory Coast
- Guinea-Bissau
- Mali
- Niger
- Senegal
- Togo
- New Caledonia
- French Polynesia
- Wallis and Futuna
- Yemen
- South Africa
- Zambia
- Zimbabwe

```
<ListView TItem="Country"
          Data="Countries"
          TextField="(item) => item.Name"
          ValueField="(item) => item.Iso"
          Mode="ListGroupMode.Static"
          MaxHeight="300px">
</ListView>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Selectable items

Set the   to .
        Bind  and provide  to setup the display text and  to uniquely identify the current active selection.

- Antarctica
- United Arab Emirates
- Afghanistan
- Albania
- Armenia
- Curacao
- Sint Maarten
- Netherlands Antilles
- Angola
- Argentina
- Australia
- Cocos Islands
- Christmas Island
- Heard Island and McDonald Islands
- Kiribati
- Norfolk Island
- Nauru
- Tuvalu
- Aruba
- Azerbaijan
- Bosnia and Herzegovina
- Barbados
- Bangladesh
- Bulgaria
- Bahrain
- Burundi
- Bermuda
- Brunei
- Bolivia
- Brazil
- Bahamas
- Bhutan
- Botswana
- Belarus
- Belize
- Canada
- Democratic Republic of the Congo
- Switzerland
- Liechtenstein
- Chile
- China
- Colombia
- Costa Rica
- Cuba
- Cape Verde
- Czech Republic
- Djibouti
- Denmark
- Faroe Islands
- Greenland
- Dominican Republic
- Algeria
- Egypt
- Eritrea
- Ethiopia
- Andorra
- Austria
- Aland Islands
- Belgium
- Saint Barthelemy
- Cyprus
- Germany
- Estonia
- Spain
- Finland
- France
- French Guiana
- Guadeloupe
- Greece
- Ireland
- Italy
- Kosovo
- Luxembourg
- Monaco
- Montenegro
- Saint Martin
- Martinique
- Malta
- Netherlands
- Saint Pierre and Miquelon
- Portugal
- Reunion
- Slovenia
- Slovakia
- San Marino
- French Southern Territories
- Vatican
- Mayotte
- Fiji
- Falkland Islands
- United Kingdom
- Guernsey
- South Georgia and the South Sandwich Islands
- Isle of Man
- Jersey
- Georgia
- Ghana
- Gibraltar
- Gambia
- Guinea
- Guatemala
- Guyana
- Hong Kong
- Honduras
- Croatia
- Haiti
- Hungary
- Indonesia
- Israel
- Palestinian Territory
- India
- Iraq
- Iran
- Iceland
- Jamaica
- Jordan
- Japan
- Kenya
- Kyrgyzstan
- Cambodia
- Comoros
- North Korea
- South Korea
- Kuwait
- Cayman Islands
- Kazakhstan
- Laos
- Lebanon
- Sri Lanka
- Liberia
- Lesotho
- Lithuania
- Latvia
- Libya
- Western Sahara
- Morocco
- Moldova
- Madagascar
- Macedonia
- Myanmar
- Mongolia
- Macao
- Mauritania
- Mauritius
- Maldives
- Malawi
- Mexico
- Malaysia
- Mozambique
- Namibia
- Nigeria
- Nicaragua
- Bouvet Island
- Norway
- Svalbard and Jan Mayen
- Nepal
- Cook Islands
- Niue
- New Zealand
- Pitcairn
- Tokelau
- Oman
- Panama
- Peru
- Papua New Guinea
- Philippines
- Pakistan
- Poland
- Paraguay
- Qatar
- Romania
- Serbia
- Serbia and Montenegro
- Russia
- Rwanda
- Saudi Arabia
- Solomon Islands
- Seychelles
- Sudan
- Sweden
- Singapore
- Saint Helena
- Sierra Leone
- Somalia
- Suriname
- South Sudan
- Sao Tome and Principe
- Syria
- Swaziland
- Thailand
- Tajikistan
- Turkmenistan
- Tunisia
- Tonga
- Turkey
- Trinidad and Tobago
- Taiwan
- Tanzania
- Ukraine
- Uganda
- American Samoa
- Bonaire, Saint Eustatius and Saba
- Ecuador
- Micronesia
- Guam
- British Indian Ocean Territory
- Marshall Islands
- Northern Mariana Islands
- Puerto Rico
- Palau
- El Salvador
- Turks and Caicos Islands
- East Timor
- United States Minor Outlying Islands
- United States
- British Virgin Islands
- U.S. Virgin Islands
- Uruguay
- Uzbekistan
- Venezuela
- Vietnam
- Vanuatu
- Samoa
- Central African Republic
- Republic of the Congo
- Cameroon
- Gabon
- Equatorial Guinea
- Chad
- Antigua and Barbuda
- Anguilla
- Dominica
- Grenada
- Saint Kitts and Nevis
- Saint Lucia
- Montserrat
- Saint Vincent and the Grenadines
- Burkina Faso
- Benin
- Ivory Coast
- Guinea-Bissau
- Mali
- Niger
- Senegal
- Togo
- New Caledonia
- French Polynesia
- Wallis and Futuna
- Yemen
- South Africa
- Zambia
- Zimbabwe

Selected Item:

```
<ListView TItem="Country"
          Data="Countries"
          TextField="(item) => item.Name"
          ValueField="(item) => item.Iso"
          Mode="ListGroupMode.Selectable"
          MaxHeight="300px"
          @bind-SelectedItem="@selectedListViewItem">
</ListView>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected Item: @selectedListViewItem?.Name
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    private Country selectedListViewItem;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Extending with custom item content

Customize the way you display the  items by providing .

- AQ

Antarctica
- AE
Abu Dhabi
United Arab Emirates
- AF
Kabul
Afghanistan
- AL
Tirana
Albania
- AM
Yerevan
Armenia
- CW
Willemstad
Curacao
- SX
Philipsburg
Sint Maarten
- AN
Willemstad
Netherlands Antilles
- AO
Luanda
Angola
- AR
Buenos Aires
Argentina
- AU
Canberra
Australia
- CC
West Island
Cocos Islands
- CX
Flying Fish Cove
Christmas Island
- HM

Heard Island and McDonald Islands
- KI
Tarawa
Kiribati
- NF
Kingston
Norfolk Island
- NR
Yaren
Nauru
- TV
Funafuti
Tuvalu
- AW
Oranjestad
Aruba
- AZ
Baku
Azerbaijan
- BA
Sarajevo
Bosnia and Herzegovina
- BB
Bridgetown
Barbados
- BD
Dhaka
Bangladesh
- BG
Sofia
Bulgaria
- BH
Manama
Bahrain
- BI
Bujumbura
Burundi
- BM
Hamilton
Bermuda
- BN
Bandar Seri Begawan
Brunei
- BO
Sucre
Bolivia
- BR
Brasilia
Brazil
- BS
Nassau
Bahamas
- BT
Thimphu
Bhutan
- BW
Gaborone
Botswana
- BY
Minsk
Belarus
- BZ
Belmopan
Belize
- CA
Ottawa
Canada
- CD
Kinshasa
Democratic Republic of the Congo
- CH
Berne
Switzerland
- LI
Vaduz
Liechtenstein
- CL
Santiago
Chile
- CN
Beijing
China
- CO
Bogota
Colombia
- CR
San Jose
Costa Rica
- CU
Havana
Cuba
- CV
Praia
Cape Verde
- CZ
Prague
Czech Republic
- DJ
Djibouti
Djibouti
- DK
Copenhagen
Denmark
- FO
Torshavn
Faroe Islands
- GL
Nuuk
Greenland
- DO
Santo Domingo
Dominican Republic
- DZ
Algiers
Algeria
- EG
Cairo
Egypt
- ER
Asmara
Eritrea
- ET
Addis Ababa
Ethiopia
- AD
Andorra la Vella
Andorra
- AT
Vienna
Austria
- AX
Mariehamn
Aland Islands
- BE
Brussels
Belgium
- BL
Gustavia
Saint Barthelemy
- CY
Nicosia
Cyprus
- DE
Berlin
Germany
- EE
Tallinn
Estonia
- ES
Madrid
Spain
- FI
Helsinki
Finland
- FR
Paris
France
- GF
Cayenne
French Guiana
- GP
Basse-Terre
Guadeloupe
- GR
Athens
Greece
- IE
Dublin
Ireland
- IT
Rome
Italy
- XK
Pristina
Kosovo
- LU
Luxembourg
Luxembourg
- MC
Monaco
Monaco
- ME
Podgorica
Montenegro
- MF
Marigot
Saint Martin
- MQ
Fort-de-France
Martinique
- MT
Valletta
Malta
- NL
Amsterdam
Netherlands
- PM
Saint-Pierre
Saint Pierre and Miquelon
- PT
Lisbon
Portugal
- RE
Saint-Denis
Reunion
- SI
Ljubljana
Slovenia
- SK
Bratislava
Slovakia
- SM
San Marino
San Marino
- TF
Port-aux-Francais
French Southern Territories
- VA
Vatican City
Vatican
- YT
Mamoudzou
Mayotte
- FJ
Suva
Fiji
- FK
Stanley
Falkland Islands
- GB
London
United Kingdom
- GG
St Peter Port
Guernsey
- GS
Grytviken
South Georgia and the South Sandwich Islands
- IM
Douglas, Isle of Man
Isle of Man
- JE
Saint Helier
Jersey
- GE
Tbilisi
Georgia
- GH
Accra
Ghana
- GI
Gibraltar
Gibraltar
- GM
Banjul
Gambia
- GN
Conakry
Guinea
- GT
Guatemala City
Guatemala
- GY
Georgetown
Guyana
- HK
Hong Kong
Hong Kong
- HN
Tegucigalpa
Honduras
- HR
Zagreb
Croatia
- HT
Port-au-Prince
Haiti
- HU
Budapest
Hungary
- ID
Jakarta
Indonesia
- IL
Jerusalem
Israel
- PS
East Jerusalem
Palestinian Territory
- IN
New Delhi
India
- IQ
Baghdad
Iraq
- IR
Tehran
Iran
- IS
Reykjavik
Iceland
- JM
Kingston
Jamaica
- JO
Amman
Jordan
- JP
Tokyo
Japan
- KE
Nairobi
Kenya
- KG
Bishkek
Kyrgyzstan
- KH
Phnom Penh
Cambodia
- KM
Moroni
Comoros
- KP
Pyongyang
North Korea
- KR
Seoul
South Korea
- KW
Kuwait City
Kuwait
- KY
George Town
Cayman Islands
- KZ
Astana
Kazakhstan
- LA
Vientiane
Laos
- LB
Beirut
Lebanon
- LK
Colombo
Sri Lanka
- LR
Monrovia
Liberia
- LS
Maseru
Lesotho
- LT
Vilnius
Lithuania
- LV
Riga
Latvia
- LY
Tripolis
Libya
- EH
El-Aaiun
Western Sahara
- MA
Rabat
Morocco
- MD
Chisinau
Moldova
- MG
Antananarivo
Madagascar
- MK
Skopje
Macedonia
- MM
Nay Pyi Taw
Myanmar
- MN
Ulan Bator
Mongolia
- MO
Macao
Macao
- MR
Nouakchott
Mauritania
- MU
Port Louis
Mauritius
- MV
Male
Maldives
- MW
Lilongwe
Malawi
- MX
Mexico City
Mexico
- MY
Kuala Lumpur
Malaysia
- MZ
Maputo
Mozambique
- NA
Windhoek
Namibia
- NG
Abuja
Nigeria
- NI
Managua
Nicaragua
- BV

Bouvet Island
- NO
Oslo
Norway
- SJ
Longyearbyen
Svalbard and Jan Mayen
- NP
Kathmandu
Nepal
- CK
Avarua
Cook Islands
- NU
Alofi
Niue
- NZ
Wellington
New Zealand
- PN
Adamstown
Pitcairn
- TK

Tokelau
- OM
Muscat
Oman
- PA
Panama City
Panama
- PE
Lima
Peru
- PG
Port Moresby
Papua New Guinea
- PH
Manila
Philippines
- PK
Islamabad
Pakistan
- PL
Warsaw
Poland
- PY
Asuncion
Paraguay
- QA
Doha
Qatar
- RO
Bucharest
Romania
- RS
Belgrade
Serbia
- CS
Belgrade
Serbia and Montenegro
- RU
Moscow
Russia
- RW
Kigali
Rwanda
- SA
Riyadh
Saudi Arabia
- SB
Honiara
Solomon Islands
- SC
Victoria
Seychelles
- SD
Khartoum
Sudan
- SE
Stockholm
Sweden
- SG
Singapur
Singapore
- SH
Jamestown
Saint Helena
- SL
Freetown
Sierra Leone
- SO
Mogadishu
Somalia
- SR
Paramaribo
Suriname
- SS
Juba
South Sudan
- ST
Sao Tome
Sao Tome and Principe
- SY
Damascus
Syria
- SZ
Mbabane
Swaziland
- TH
Bangkok
Thailand
- TJ
Dushanbe
Tajikistan
- TM
Ashgabat
Turkmenistan
- TN
Tunis
Tunisia
- TO
Nuku'alofa
Tonga
- TR
Ankara
Turkey
- TT
Port of Spain
Trinidad and Tobago
- TW
Taipei
Taiwan
- TZ
Dodoma
Tanzania
- UA
Kiev
Ukraine
- UG
Kampala
Uganda
- AS
Pago Pago
American Samoa
- BQ

Bonaire, Saint Eustatius and Saba
- EC
Quito
Ecuador
- FM
Palikir
Micronesia
- GU
Hagatna
Guam
- IO
Diego Garcia
British Indian Ocean Territory
- MH
Majuro
Marshall Islands
- MP
Saipan
Northern Mariana Islands
- PR
San Juan
Puerto Rico
- PW
Melekeok
Palau
- SV
San Salvador
El Salvador
- TC
Cockburn Town
Turks and Caicos Islands
- TL
Dili
East Timor
- UM

United States Minor Outlying Islands
- US
Washington
United States
- VG
Road Town
British Virgin Islands
- VI
Charlotte Amalie
U.S. Virgin Islands
- UY
Montevideo
Uruguay
- UZ
Tashkent
Uzbekistan
- VE
Caracas
Venezuela
- VN
Hanoi
Vietnam
- VU
Port Vila
Vanuatu
- WS
Apia
Samoa
- CF
Bangui
Central African Republic
- CG
Brazzaville
Republic of the Congo
- CM
Yaounde
Cameroon
- GA
Libreville
Gabon
- GQ
Malabo
Equatorial Guinea
- TD
N'Djamena
Chad
- AG
St. John's
Antigua and Barbuda
- AI
The Valley
Anguilla
- DM
Roseau
Dominica
- GD
St. George's
Grenada
- KN
Basseterre
Saint Kitts and Nevis
- LC
Castries
Saint Lucia
- MS
Plymouth
Montserrat
- VC
Kingstown
Saint Vincent and the Grenadines
- BF
Ouagadougou
Burkina Faso
- BJ
Porto-Novo
Benin
- CI
Yamoussoukro
Ivory Coast
- GW
Bissau
Guinea-Bissau
- ML
Bamako
Mali
- NE
Niamey
Niger
- SN
Dakar
Senegal
- TG
Lome
Togo
- NC
Noumea
New Caledonia
- PF
Papeete
French Polynesia
- WF
Mata Utu
Wallis and Futuna
- YE
Sanaa
Yemen
- ZA
Pretoria
South Africa
- ZM
Lusaka
Zambia
- ZW
Harare
Zimbabwe

```
<ListView TItem="Country"
          Data="Countries"
          TextField="(item) => item.Name"
          ValueField="(item) => item.Iso"
          Mode="ListGroupMode.Static"
          MaxHeight="300px">
    <ItemTemplate>
        <Div Flex="Flex.InlineFlex.JustifyContent.Between" Width="Width.Is100">
            <Heading Margin="Margin.Is2.FromBottom">@context.Item.Iso</Heading>
            <Small>@context.Item.Capital</Small>
        </Div>
        <Paragraph Margin="Margin.Is2.FromBottom">@context.Text</Paragraph>
    </ItemTemplate>
</ListView>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Styling Individual Items

Customize the look of each item by using the right callbacks.

- Antarctica
- United Arab Emirates
- Afghanistan
- Albania
- Armenia
- Curacao
- Sint Maarten
- Netherlands Antilles
- Angola
- Argentina
- Australia
- Cocos Islands
- Christmas Island
- Heard Island and McDonald Islands
- Kiribati
- Norfolk Island
- Nauru
- Tuvalu
- Aruba
- Azerbaijan
- Bosnia and Herzegovina
- Barbados
- Bangladesh
- Bulgaria
- Bahrain
- Burundi
- Bermuda
- Brunei
- Bolivia
- Brazil
- Bahamas
- Bhutan
- Botswana
- Belarus
- Belize
- Canada
- Democratic Republic of the Congo
- Switzerland
- Liechtenstein
- Chile
- China
- Colombia
- Costa Rica
- Cuba
- Cape Verde
- Czech Republic
- Djibouti
- Denmark
- Faroe Islands
- Greenland
- Dominican Republic
- Algeria
- Egypt
- Eritrea
- Ethiopia
- Andorra
- Austria
- Aland Islands
- Belgium
- Saint Barthelemy
- Cyprus
- Germany
- Estonia
- Spain
- Finland
- France
- French Guiana
- Guadeloupe
- Greece
- Ireland
- Italy
- Kosovo
- Luxembourg
- Monaco
- Montenegro
- Saint Martin
- Martinique
- Malta
- Netherlands
- Saint Pierre and Miquelon
- Portugal
- Reunion
- Slovenia
- Slovakia
- San Marino
- French Southern Territories
- Vatican
- Mayotte
- Fiji
- Falkland Islands
- United Kingdom
- Guernsey
- South Georgia and the South Sandwich Islands
- Isle of Man
- Jersey
- Georgia
- Ghana
- Gibraltar
- Gambia
- Guinea
- Guatemala
- Guyana
- Hong Kong
- Honduras
- Croatia
- Haiti
- Hungary
- Indonesia
- Israel
- Palestinian Territory
- India
- Iraq
- Iran
- Iceland
- Jamaica
- Jordan
- Japan
- Kenya
- Kyrgyzstan
- Cambodia
- Comoros
- North Korea
- South Korea
- Kuwait
- Cayman Islands
- Kazakhstan
- Laos
- Lebanon
- Sri Lanka
- Liberia
- Lesotho
- Lithuania
- Latvia
- Libya
- Western Sahara
- Morocco
- Moldova
- Madagascar
- Macedonia
- Myanmar
- Mongolia
- Macao
- Mauritania
- Mauritius
- Maldives
- Malawi
- Mexico
- Malaysia
- Mozambique
- Namibia
- Nigeria
- Nicaragua
- Bouvet Island
- Norway
- Svalbard and Jan Mayen
- Nepal
- Cook Islands
- Niue
- New Zealand
- Pitcairn
- Tokelau
- Oman
- Panama
- Peru
- Papua New Guinea
- Philippines
- Pakistan
- Poland
- Paraguay
- Qatar
- Romania
- Serbia
- Serbia and Montenegro
- Russia
- Rwanda
- Saudi Arabia
- Solomon Islands
- Seychelles
- Sudan
- Sweden
- Singapore
- Saint Helena
- Sierra Leone
- Somalia
- Suriname
- South Sudan
- Sao Tome and Principe
- Syria
- Swaziland
- Thailand
- Tajikistan
- Turkmenistan
- Tunisia
- Tonga
- Turkey
- Trinidad and Tobago
- Taiwan
- Tanzania
- Ukraine
- Uganda
- American Samoa
- Bonaire, Saint Eustatius and Saba
- Ecuador
- Micronesia
- Guam
- British Indian Ocean Territory
- Marshall Islands
- Northern Mariana Islands
- Puerto Rico
- Palau
- El Salvador
- Turks and Caicos Islands
- East Timor
- United States Minor Outlying Islands
- United States
- British Virgin Islands
- U.S. Virgin Islands
- Uruguay
- Uzbekistan
- Venezuela
- Vietnam
- Vanuatu
- Samoa
- Central African Republic
- Republic of the Congo
- Cameroon
- Gabon
- Equatorial Guinea
- Chad
- Antigua and Barbuda
- Anguilla
- Dominica
- Grenada
- Saint Kitts and Nevis
- Saint Lucia
- Montserrat
- Saint Vincent and the Grenadines
- Burkina Faso
- Benin
- Ivory Coast
- Guinea-Bissau
- Mali
- Niger
- Senegal
- Togo
- New Caledonia
- French Polynesia
- Wallis and Futuna
- Yemen
- South Africa
- Zambia
- Zimbabwe

Selected Item:

```
@using System.Linq

<ListView TItem="Country"
          Data="Countries"
          TextField="(item) => item.Name"
          ValueField="(item) => item.Iso"
          Mode="ListGroupMode.Selectable"
          MaxHeight="300px"
          ItemTextColor="((item) => Countries.IndexOf( item ) % 2 == 0 ? TextColor.Danger : TextColor.Success)"
          ItemBackground="(item) => Background.Default"
          ItemPadding="(item) => Padding.Is4"
          ItemClass="@((item) => $"country-{item.Iso}")"
          ItemStyle="@((item) => "border: 1px solid red")"
          @bind-SelectedItem="@selectedListViewItem">
</ListView>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected Item: @selectedListViewItem?.Name
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public List<Country> Countries;

    private Country selectedListViewItem;

    protected override async Task OnInitializedAsync()
    {
        Countries = (await CountryData.GetDataAsync()).ToList();
        await base.OnInitializedAsync();
    }
}
```

## API

### Parameters

| Parameter     | Description                                                                                                          | Type                               | Default   |
|---------------|----------------------------------------------------------------------------------------------------------------------|------------------------------------|-----------|
| Attributes    | Captures all the custom attribute that are not part of Blazorise component.                                          | Dictionary<string, object>         | null      |
| ChildContent  | Specifies the content to be rendered inside this Components.ListView.                                                | RenderFragment                     | null      |
| Class         | Custom css class-names.                                                                                              | string                             |           |
| Data          | Gets or sets the items data-source.                                                                                  | IEnumerable<TItem>                 | null      |
| Flush         | Remove some borders and rounded corners to render list group items edge-to-edge in a parent container (e.g., cards). | bool                               | false     |
| Height        | Sets the ListView Height.      Defaults to empty.                                                                    | string                             |           |
| ItemTemplate  | Specifies the content to be rendered inside each item of the Components.ListView.                                    | RenderFragment<ItemContext<TItem>> | null      |
| MaxHeight     | Sets the ListView MaxHeight.      Defaults to 250px.                                                                 | string                             | "250px"   |
| Mode          | Defines the list-group behavior mode.Possible values:Static, Selectable                                              | ListGroupMode                      | Static    |
| Scrollable    | Makes the list group scrollable by adding a vertical scrollbar.                                                      | bool                               | true      |
| SelectedItem  | Currently selected item.                                                                                             | TItem                              | null      |
| SelectedItems | Currently selected items.                                                                                            | List<TItem>                        | null      |
| SelectionMode | Defines the list-group selection mode.Possible values:Single, Multiple                                               | ListGroupSelectionMode             | Single    |
| Style         | Custom styles.                                                                                                       | string                             |           |
| Virtualize    | Gets or sets whether the listview will use the Virtualize functionality.                                             | bool                               | false     |

### Events

| Event                | Description                                                          | Type                        |
|----------------------|----------------------------------------------------------------------|-----------------------------|
| DisabledItem         | Method used to get the disabled items from the supplied data source. | Func<TItem, bool>           |
| ItemBackground       | Method used to get the background color for the item.                | Func<TItem, Background>     |
| ItemClass            | Method used to get the class for the item.                           | Func<TItem, string>         |
| ItemMargin           | Method used to get the margin for the item.                          | Func<TItem, IFluentSpacing> |
| ItemPadding          | Method used to get the padding for the item.                         | Func<TItem, IFluentSpacing> |
| ItemStyle            | Method used to get the style for the item.                           | Func<TItem, string>         |
| ItemTextColor        | Method used to get the text color for the item.                      | Func<TItem, TextColor>      |
| SelectedItemChanged  | Occurs after the selected item has changed.                          | EventCallback<TItem>        |
| SelectedItemsChanged | Occurs after the selected items has changed.                         | EventCallback<List<TItem>>  |
| TextField            | Method used to get the display field from the supplied data source.  | Func<TItem, string>         |
| ValueField           | Method used to get the value field from the supplied data source.    | Func<TItem, string>         |

###### On this page

#### 

## 