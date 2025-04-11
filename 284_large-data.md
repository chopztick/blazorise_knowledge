# Blazorise DataGrid: Large Data

The DataGrid Read Data feature allows you to handle Large Data by providing you with a centralized ReadData Method that allows you to query your data by pages.

### Large Data

By default, DataGrid will load everything in memory and it will perform the necessary operations like paging, sorting and filtering. For large datasets this is impractical and so for these scenarios it is advised to load data page-by-page.

This is accomplished with the use of ReadData event handler and TotalItems attribute. When you define the usage of ReadData the DataGrid will automatically switch to manual mode and every interaction with the grid will be proxied through the ReadData. This means that you as a developer will be responsible for all the loading, filtering and sorting of the data.

- ReadData event handler used to handle the loading of data
- TotalItems total number of items in the source data-set

Bellow you can find a basic example of how to load large data and apply it to the DataGrid.

            Just as in the previous example everything is the same except that now we must define the attribute ReadData and TotalItems. They’re used to handle all of the loading, filtering and sorting of an actual data.

Additionally you will find the support for generating an ODataQuery by using the provided extension ToODataString.

|   # | First Name   | Last Name    | Salary      |
|-----|--------------|--------------|-------------|
|   1 | Samuel       | Collier      | 86 030,41 € |
|   2 | Irvin        | Ziemann      | 61 781,31 € |
|   3 | Gerald       | Pollich      | 58 810,75 € |
|   4 | Cora         | Conn         | 84 414,66 € |
|   5 | Alfonso      | D'Amore      | 69 318,29 € |
|   6 | Jessie       | Wilkinson    | 78 566,12 € |
|   7 | Gregory      | Renner       | 57 456,82 € |
|   8 | Maryann      | Hilpert      | 89 153,38 € |
|   9 | Merle        | Pacocha      | 55 349,94 € |
|  10 | Angelina     | Ward         | 73 625,86 € |
|  11 | Kara         | Brekke       | 58 321,87 € |
|  12 | Yvette       | Ferry        | 89 658,90 € |
|  13 | Pablo        | Friesen      | 77 090,27 € |
|  14 | Ernest       | Homenick     | 54 910,14 € |
|  15 | Leslie       | Wehner       | 78 930,58 € |
|  16 | Miguel       | Lynch        | 65 348,06 € |
|  17 | Tommy        | Swaniawski   | 92 326,27 € |
|  18 | Viola        | Wilderman    | 76 575,00 € |
|  19 | Brenda       | Jacobson     | 86 145,68 € |
|  20 | Roger        | Herzog       | 53 168,45 € |
|  21 | Casey        | Weber        | 56 257,49 € |
|  22 | Tara         | Schoen       | 72 637,29 € |
|  23 | Al           | Sanford      | 88 870,12 € |
|  24 | Jill         | Stokes       | 59 252,89 € |
|  25 | Marian       | Armstrong    | 69 182,74 € |
|  26 | Janie        | Stanton      | 51 608,79 € |
|  27 | Dixie        | Block        | 89 653,26 € |
|  28 | Teresa       | Dietrich     | 56 151,34 € |
|  29 | Renee        | Herzog       | 93 592,47 € |
|  30 | Damon        | Lubowitz     | 89 271,37 € |
|  31 | Cody         | Rau          | 63 067,69 € |
|  32 | Ethel        | Kassulke     | 92 175,30 € |
|  33 | Rudy         | Walsh        | 76 356,17 € |
|  34 | Ross         | Hauck        | 51 620,31 € |
|  35 | Otis         | Little       | 77 906,94 € |
|  36 | Benjamin     | Friesen      | 78 343,54 € |
|  37 | Moses        | Mosciski     | 99 202,48 € |
|  38 | Kellie       | Murazik      | 98 314,89 € |
|  39 | Nichole      | Keebler      | 65 412,00 € |
|  40 | Bobbie       | Rogahn       | 52 889,16 € |
|  41 | Charlie      | Borer        | 50 448,59 € |
|  42 | Luis         | Rutherford   | 83 594,06 € |
|  43 | Jared        | Pfannerstill | 54 282,76 € |
|  44 | Floyd        | Satterfield  | 59 157,17 € |
|  45 | Claude       | Parker       | 58 576,97 € |
|  46 | Donald       | Daugherty    | 66 692,86 € |
|  47 | Roland       | Bruen        | 98 404,23 € |
|  48 | Pauline      | Conroy       | 69 674,96 € |
|  49 | Lora         | Lockman      | 74 035,99 € |
|  50 | Joey         | Koelpin      | 57 184,86 € |
|  51 | Stacey       | Graham       | 88 562,39 € |
|  52 | Daisy        | Medhurst     | 51 011,13 € |
|  53 | Erin         | Corwin       | 70 013,81 € |
|  54 | Arturo       | Denesik      | 61 456,56 € |
|  55 | Cheryl       | Collier      | 59 868,88 € |
|  56 | Andres       | Williamson   | 74 180,71 € |
|  57 | Phyllis      | Wilderman    | 59 518,29 € |
|  58 | Billy        | Wiza         | 92 241,90 € |
|  59 | Woodrow      | Gibson       | 90 288,10 € |
|  60 | Cristina     | Harris       | 81 762,53 € |
|  61 | Darlene      | Daniel       | 74 142,55 € |
|  62 | Courtney     | Frami        | 68 435,70 € |
|  63 | Mae          | Feeney       | 65 623,26 € |
|  64 | Josh         | Doyle        | 87 057,60 € |
|  65 | Gwen         | Abbott       | 65 189,89 € |
|  66 | Mona         | Beier        | 80 367,71 € |
|  67 | Minnie       | Corwin       | 78 002,56 € |
|  68 | Dwight       | Runolfsson   | 73 986,40 € |
|  69 | Beth         | Bartell      | 85 841,65 € |
|  70 | Steve        | Schulist     | 94 190,45 € |
|  71 | Pam          | Greenholt    | 75 695,28 € |
|  72 | Darrel       | Williamson   | 70 327,72 € |
|  73 | Rolando      | Sauer        | 84 971,22 € |
|  74 | Cesar        | Schaefer     | 92 704,04 € |
|  75 | Luis         | Leannon      | 61 167,01 € |
|  76 | Fannie       | Williamson   | 94 194,50 € |
|  77 | Marianne     | Pouros       | 71 394,54 € |
|  78 | Spencer      | Rogahn       | 55 993,84 € |
|  79 | Donnie       | Luettgen     | 77 655,38 € |
|  80 | Blanca       | Breitenberg  | 75 633,97 € |
|  81 | Pat          | Rohan        | 50 151,72 € |
|  82 | Virginia     | Kassulke     | 77 411,81 € |
|  83 | Lela         | Breitenberg  | 53 894,64 € |
|  84 | Randal       | Koss         | 93 602,37 € |
|  85 | Kimberly     | Christiansen | 65 089,52 € |
|  86 | Jean         | Boyer        | 99 805,01 € |
|  87 | Muriel       | Shields      | 66 809,95 € |
|  88 | Marcus       | Emmerich     | 99 401,27 € |
|  89 | Faith        | Nicolas      | 50 439,25 € |
|  90 | Boyd         | Davis        | 58 591,48 € |
|  91 | Wilbur       | Stiedemann   | 64 479,16 € |
|  92 | Roberto      | Stracke      | 57 007,18 € |
|  93 | Mindy        | Smitham      | 56 810,55 € |
|  94 | Dianne       | Maggio       | 73 990,94 € |
|  95 | Mandy        | Bahringer    | 69 018,94 € |
|  96 | Marlon       | Ledner       | 72 372,09 € |
|  97 | Laverne      | Schuster     | 84 767,07 € |
|  98 | Kendra       | Corkery      | 79 303,18 € |
|  99 | Chris        | Barton       | 68 642,57 € |
| 100 | Ed           | Price        | 84 665,20 € |
| 101 | Tracey       | Durgan       | 63 539,54 € |
| 102 | Alyssa       | Gaylord      | 92 963,65 € |
| 103 | Helen        | Mueller      | 51 704,43 € |
| 104 | Ronald       | Moen         | 88 173,43 € |
| 105 | Gerard       | McDermott    | 79 616,46 € |
| 106 | Samantha     | Zboncak      | 75 298,13 € |
| 107 | Van          | Gleichner    | 90 917,71 € |
| 108 | Frederick    | Bode         | 52 949,98 € |
| 109 | Lela         | Gutmann      | 52 247,22 € |
| 110 | Harvey       | Gutmann      | 82 998,73 € |
| 111 | Luis         | Robel        | 91 952,69 € |
| 112 | Brandi       | Ward         | 70 341,50 € |
| 113 | Margie       | Hills        | 93 092,75 € |
| 114 | Toby         | Beatty       | 66 829,50 € |
| 115 | Bobby        | Ward         | 82 475,01 € |
| 116 | Jason        | Barrows      | 87 777,57 € |
| 117 | Francis      | Ullrich      | 69 615,22 € |
| 118 | Herman       | Marquardt    | 84 744,26 € |
| 119 | Francis      | Gleason      | 58 666,45 € |
| 120 | Carolyn      | Kunze        | 80 404,42 € |
| 121 | Terry        | Rogahn       | 69 352,10 € |
| 122 | Kendra       | Senger       | 93 641,61 € |
| 123 | Rochelle     | Kessler      | 96 931,95 € |
| 124 | Yvonne       | Halvorson    | 94 598,15 € |
| 125 | Kendra       | Bernhard     | 59 931,41 € |
| 126 | Katherine    | Price        | 60 998,60 € |
| 127 | Lillian      | Wyman        | 52 545,83 € |
| 128 | Velma        | Wunsch       | 74 742,06 € |
| 129 | Kristy       | Herman       | 96 811,63 € |
| 130 | Erick        | Parker       | 88 902,23 € |
| 131 | Dean         | Johnston     | 72 987,32 € |
| 132 | Phillip      | Brekke       | 69 227,78 € |
| 133 | Ashley       | Blick        | 74 736,25 € |
| 134 | Larry        | Feeney       | 76 448,86 € |
| 135 | Kayla        | Glover       | 97 369,33 € |
| 136 | Alvin        | Simonis      | 62 546,08 € |
| 137 | Kevin        | Kassulke     | 80 076,32 € |
| 138 | Teresa       | O'Kon        | 87 065,63 € |
| 139 | Ella         | Cartwright   | 90 099,49 € |
| 140 | Albert       | Howe         | 50 647,80 € |
| 141 | Andrew       | Pfeffer      | 99 691,54 € |
| 142 | Garrett      | Jenkins      | 56 963,04 € |
| 143 | Louis        | Kuvalis      | 80 519,61 € |
| 144 | Myrtle       | Tromp        | 69 930,94 € |
| 145 | Andrew       | Murphy       | 55 579,15 € |
| 146 | Patricia     | Gaylord      | 89 805,17 € |
| 147 | Preston      | Kuvalis      | 83 615,78 € |
| 148 | Merle        | Osinski      | 92 220,65 € |
| 149 | Alberto      | Bernhard     | 52 655,29 € |
| 150 | Darrell      | Beatty       | 54 224,58 € |
| 151 | Joanne       | Bartoletti   | 53 083,34 € |
| 152 | Gloria       | Bahringer    | 65 360,79 € |
| 153 | Cameron      | Hane         | 74 440,82 € |
| 154 | Conrad       | Dooley       | 79 099,12 € |
| 155 | Erik         | Marks        | 93 408,43 € |
| 156 | Carolyn      | Wolff        | 97 583,81 € |
| 157 | Silvia       | O'Hara       | 72 185,23 € |
| 158 | Dexter       | Hettinger    | 90 261,40 € |
| 159 | Margaret     | Ledner       | 62 783,44 € |
| 160 | Ellis        | Herzog       | 60 940,26 € |
| 161 | Merle        | Bahringer    | 53 660,05 € |
| 162 | Roberto      | Yost         | 61 169,10 € |
| 163 | Stacy        | Kuhlman      | 93 823,76 € |
| 164 | Corey        | Monahan      | 57 966,22 € |
| 165 | Chelsea      | Sawayn       | 52 049,90 € |
| 166 | Clifton      | Mills        | 68 356,52 € |
| 167 | Teri         | Kling        | 67 176,87 € |
| 168 | Tanya        | Farrell      | 58 393,52 € |
| 169 | Marianne     | Carroll      | 92 390,80 € |
| 170 | Rosalie      | Purdy        | 86 463,78 € |
| 171 | Shirley      | Greenfelder  | 91 685,68 € |
| 172 | Delores      | Steuber      | 94 113,92 € |
| 173 | Terri        | Klein        | 68 647,08 € |
| 174 | Marjorie     | Beahan       | 84 706,53 € |
| 175 | Reginald     | Reinger      | 85 323,79 € |
| 176 | Kelley       | Bode         | 79 071,76 € |
| 177 | Loren        | Howell       | 93 204,93 € |
| 178 | Lindsey      | Smith        | 99 085,43 € |
| 179 | Doug         | Wilkinson    | 79 267,68 € |
| 180 | Bernadette   | Watsica      | 77 302,18 € |
| 181 | Billy        | Volkman      | 68 235,94 € |
| 182 | Courtney     | Reinger      | 54 541,73 € |
| 183 | Marjorie     | Dietrich     | 51 211,89 € |
| 184 | Meghan       | Pollich      | 62 102,58 € |
| 185 | Phillip      | Smitham      | 79 097,74 € |
| 186 | Verna        | Klocko       | 66 963,02 € |
| 187 | Rodolfo      | Mertz        | 57 742,48 € |
| 188 | Sabrina      | Hyatt        | 82 874,64 € |
| 189 | Roger        | Lehner       | 85 927,11 € |
| 190 | Julia        | Huels        | 67 309,00 € |
| 191 | May          | Reynolds     | 96 990,64 € |
| 192 | Bennie       | Williamson   | 67 591,28 € |
| 193 | Evan         | Okuneva      | 79 220,93 € |
| 194 | Diana        | Rohan        | 78 141,34 € |
| 195 | Shari        | Smitham      | 60 195,83 € |
| 196 | Ella         | Schiller     | 83 482,98 € |
| 197 | Karen        | Towne        | 54 088,60 € |
| 198 | Kelly        | Jones        | 78 290,86 € |
| 199 | Robin        | Lesch        | 66 805,27 € |
| 200 | Guy          | Mayert       | 68 127,67 € |
| 201 | Misty        | Ondricka     | 75 954,94 € |
| 202 | Julius       | White        | 78 706,96 € |
| 203 | Josh         | Gaylord      | 60 487,10 € |
| 204 | Debra        | Johnston     | 83 953,91 € |
| 205 | Kellie       | Marks        | 64 800,44 € |
| 206 | Taylor       | Goodwin      | 83 261,10 € |
| 207 | Lee          | Metz         | 98 403,81 € |
| 208 | Eddie        | Murazik      | 68 029,89 € |
| 209 | Ernesto      | McLaughlin   | 99 436,01 € |
| 210 | Laurence     | Turner       | 51 909,85 € |
| 211 | Hazel        | Vandervort   | 94 267,75 € |
| 212 | Cecelia      | Nader        | 74 472,40 € |
| 213 | Phil         | Ledner       | 68 881,51 € |
| 214 | Krystal      | Metz         | 83 250,52 € |
| 215 | Don          | Altenwerth   | 52 897,75 € |
| 216 | Candace      | McCullough   | 96 247,14 € |
| 217 | Sabrina      | Gulgowski    | 50 276,69 € |
| 218 | Laurence     | Batz         | 64 410,12 € |
| 219 | Shane        | Rippin       | 75 551,08 € |
| 220 | Bernadette   | Morissette   | 98 512,13 € |
| 221 | Alexander    | West         | 61 698,25 € |
| 222 | Stella       | McKenzie     | 78 466,06 € |
| 223 | Arlene       | Parker       | 57 641,64 € |
| 224 | Brett        | Durgan       | 67 162,65 € |
| 225 | Muriel       | Tremblay     | 78 588,45 € |
| 226 | Adam         | Upton        | 88 672,89 € |
| 227 | Lester       | Bartell      | 59 093,66 € |
| 228 | Cristina     | Streich      | 81 916,04 € |
| 229 | Ernestine    | Heathcote    | 71 069,20 € |
| 230 | Clarence     | Emard        | 82 071,65 € |
| 231 | Mona         | Kertzmann    | 56 353,15 € |
| 232 | Tracey       | Pfeffer      | 91 484,81 € |
| 233 | Tony         | Hartmann     | 80 992,77 € |
| 234 | Harry        | Treutel      | 51 423,99 € |
| 235 | Ervin        | Tillman      | 82 561,69 € |
| 236 | Derek        | Schoen       | 95 956,53 € |
| 237 | Anthony      | Price        | 74 884,58 € |
| 238 | Shari        | Zboncak      | 96 737,83 € |
| 239 | Glenn        | Leannon      | 63 534,18 € |
| 240 | Guy          | Treutel      | 60 108,71 € |
| 241 | Angie        | Hoppe        | 65 635,04 € |
| 242 | Catherine    | Bartell      | 98 196,01 € |
| 243 | Timmy        | Torp         | 54 958,10 € |
| 244 | Walter       | Schimmel     | 51 050,65 € |
| 245 | Cecilia      | Lakin        | 95 127,62 € |
| 246 | Colin        | Reichel      | 66 112,87 € |
| 247 | Victoria     | Deckow       | 60 492,50 € |
| 248 | Homer        | Cormier      | 90 229,04 € |
| 249 | Spencer      | O'Reilly     | 60 243,52 € |
| 250 | Allan        | Hand         | 59 170,08 € |
| 251 | Cameron      | Ondricka     | 79 858,60 € |
| 252 | Mark         | Bins         | 52 790,83 € |
| 253 | Jaime        | Jacobson     | 76 493,75 € |
| 254 | Irma         | Watsica      | 58 546,05 € |
| 255 | Shaun        | Braun        | 59 642,92 € |
| 256 | Diana        | Effertz      | 82 583,67 € |
| 257 | Steven       | Dooley       | 64 657,62 € |
| 258 | Irma         | Kovacek      | 94 208,96 € |
| 259 | Emmett       | Herzog       | 67 817,81 € |
| 260 | Kelly        | Davis        | 71 400,98 € |
| 261 | Luz          | Morar        | 64 577,48 € |
| 262 | Marta        | Harris       | 66 971,72 € |
| 263 | Mabel        | Wolff        | 74 724,96 € |
| 264 | Samuel       | Gutkowski    | 60 034,46 € |
| 265 | Emma         | Emmerich     | 72 648,66 € |
| 266 | Irvin        | Mitchell     | 50 003,10 € |
| 267 | Nicolas      | Halvorson    | 71 526,27 € |
| 268 | Charlie      | Jerde        | 73 030,99 € |
| 269 | Ramona       | Dibbert      | 74 358,11 € |
| 270 | Clifton      | Klein        | 97 270,09 € |
| 271 | Stella       | Steuber      | 59 692,64 € |
| 272 | Juanita      | Champlin     | 72 780,75 € |
| 273 | Isaac        | Stamm        | 69 292,97 € |
| 274 | Doyle        | Schumm       | 51 427,45 € |
| 275 | Clay         | Grimes       | 51 772,08 € |
| 276 | Roland       | Mayert       | 81 883,80 € |
| 277 | Edmond       | Bahringer    | 50 929,17 € |
| 278 | Randall      | Daniel       | 89 905,30 € |
| 279 | Gregory      | Spencer      | 74 161,60 € |
| 280 | Owen         | Swaniawski   | 95 707,25 € |
| 281 | Laverne      | Pacocha      | 65 789,34 € |
| 282 | Sara         | Shields      | 86 180,98 € |
| 283 | Christian    | Hoeger       | 71 363,32 € |
| 284 | Damon        | Denesik      | 55 400,84 € |
| 285 | Marjorie     | Emmerich     | 63 652,59 € |
| 286 | Tasha        | Borer        | 94 186,62 € |
| 287 | Joseph       | Kris         | 67 814,68 € |
| 288 | Bethany      | Beer         | 65 998,18 € |
| 289 | Terrance     | Thiel        | 80 137,01 € |
| 290 | Bob          | Casper       | 68 748,43 € |
| 291 | Joe          | Lakin        | 98 278,19 € |
| 292 | Lee          | Wolff        | 94 738,69 € |
| 293 | Alvin        | Smith        | 68 593,23 € |
| 294 | Jimmie       | Dietrich     | 84 267,88 € |
| 295 | Tyrone       | Dach         | 94 728,32 € |
| 296 | Van          | Mills        | 60 109,47 € |
| 297 | Ted          | Gibson       | 65 825,81 € |
| 298 | Roxanne      | Kuhn         | 79 023,74 € |
| 299 | Regina       | Keeling      | 66 369,94 € |
| 300 | Helen        | Witting      | 74 575,87 € |
| 301 | Oliver       | Daniel       | 54 641,11 € |
| 302 | Doug         | Leannon      | 76 076,55 € |
| 303 | Carol        | Schmeler     | 83 833,88 € |
| 304 | Don          | Mills        | 53 632,72 € |
| 305 | Lindsey      | Considine    | 98 571,25 € |
| 306 | Grace        | Nader        | 82 399,49 € |
| 307 | Candice      | Rodriguez    | 90 887,74 € |
| 308 | Lula         | Schultz      | 97 039,29 € |
| 309 | Lee          | Bins         | 71 842,44 € |
| 310 | Saul         | Howe         | 52 676,35 € |
| 311 | Louise       | Gislason     | 88 305,26 € |
| 312 | Myrtle       | Hackett      | 68 996,49 € |
| 313 | Casey        | Zemlak       | 57 259,51 € |
| 314 | Kristen      | Huel         | 54 689,50 € |
| 315 | Krista       | Kris         | 93 758,65 € |
| 316 | Danielle     | Jerde        | 99 301,40 € |
| 317 | Angelica     | Tremblay     | 85 313,90 € |
| 318 | Louise       | Abshire      | 77 784,92 € |
| 319 | Wm           | Bogisich     | 62 126,09 € |
| 320 | Maryann      | Wisoky       | 85 135,69 € |
| 321 | Betsy        | Wisozk       | 77 627,62 € |
| 322 | Alexander    | Stoltenberg  | 99 611,36 € |
| 323 | Judith       | Flatley      | 77 310,19 € |
| 324 | Stewart      | Treutel      | 50 889,65 € |
| 325 | Helen        | Schiller     | 73 442,69 € |
| 326 | Heidi        | Haag         | 51 397,29 € |
| 327 | Ross         | Thiel        | 92 754,54 € |
| 328 | Amanda       | Senger       | 89 441,31 € |
| 329 | Beth         | Hilpert      | 62 114,78 € |
| 330 | Curtis       | Hessel       | 57 498,77 € |
| 331 | Alma         | Gibson       | 90 762,65 € |
| 332 | Jeannette    | Schaden      | 96 075,03 € |
| 333 | Roberto      | Herman       | 97 894,29 € |
| 334 | Clarence     | Blanda       | 50 450,45 € |
| 335 | Jeffery      | Kassulke     | 55 046,88 € |
| 336 | Trevor       | Schuppe      | 80 338,20 € |
| 337 | Ron          | Lebsack      | 55 184,82 € |
| 338 | Cedric       | Auer         | 67 321,90 € |
| 339 | Gina         | Schiller     | 89 055,19 € |
| 340 | Julius       | Schmidt      | 69 183,31 € |
| 341 | Brandi       | Corkery      | 67 152,53 € |
| 342 | Alicia       | McClure      | 93 251,90 € |
| 343 | Michele      | Waters       | 92 624,38 € |
| 344 | Kristen      | Hoeger       | 60 848,20 € |
| 345 | Kate         | Heathcote    | 62 751,58 € |
| 346 | Rudolph      | Leffler      | 90 085,95 € |
| 347 | Garry        | McCullough   | 87 440,86 € |
| 348 | Tracey       | Rutherford   | 71 584,47 € |
| 349 | Shelly       | Bartoletti   | 95 964,97 € |
| 350 | Johnny       | Padberg      | 91 804,24 € |
| 351 | David        | Smitham      | 68 092,90 € |
| 352 | Priscilla    | Conroy       | 92 922,27 € |
| 353 | Shannon      | Emard        | 53 804,17 € |
| 354 | Paula        | Kautzer      | 53 365,86 € |
| 355 | Jay          | Douglas      | 62 473,03 € |
| 356 | Wesley       | Torphy       | 54 390,81 € |
| 357 | Lorraine     | Williamson   | 80 333,70 € |
| 358 | Johanna      | Hahn         | 55 954,42 € |
| 359 | Alexander    | Mertz        | 99 571,59 € |
| 360 | Wilson       | Bruen        | 64 776,40 € |
| 361 | Hubert       | Pfannerstill | 63 008,59 € |
| 362 | Alan         | O'Kon        | 80 885,59 € |
| 363 | Willie       | Metz         | 51 930,24 € |
| 364 | Joey         | Ferry        | 94 608,69 € |
| 365 | Ricky        | Hermann      | 83 772,49 € |
| 366 | Devin        | Stamm        | 94 867,24 € |
| 367 | Joshua       | Homenick     | 76 817,11 € |
| 368 | Larry        | Daugherty    | 73 207,94 € |
| 369 | Claude       | Gleason      | 85 370,52 € |
| 370 | Sammy        | Murazik      | 69 384,89 € |
| 371 | Angelina     | Abshire      | 60 717,13 € |
| 372 | Tasha        | Kunze        | 64 904,36 € |
| 373 | Lula         | Collier      | 90 212,24 € |
| 374 | Deanna       | Stiedemann   | 78 268,35 € |
| 375 | Shelley      | Johns        | 87 217,90 € |
| 376 | Albert       | Little       | 81 290,85 € |
| 377 | Carlos       | Reichel      | 98 138,19 € |
| 378 | Ebony        | Schiller     | 68 048,74 € |
| 379 | Andrew       | Schultz      | 60 699,23 € |
| 380 | Ebony        | Strosin      | 62 514,96 € |
| 381 | Janet        | Hauck        | 84 912,58 € |
| 382 | Darryl       | Barton       | 52 279,26 € |
| 383 | Lawrence     | Reilly       | 69 375,45 € |
| 384 | Merle        | Abbott       | 68 595,59 € |
| 385 | Hugo         | O'Conner     | 83 359,23 € |
| 386 | Janice       | Rodriguez    | 80 747,25 € |
| 387 | Sabrina      | Rohan        | 87 173,33 € |
| 388 | Carrie       | Rutherford   | 60 272,93 € |
| 389 | Dexter       | Mayert       | 76 548,50 € |
| 390 | Neil         | Collier      | 65 578,63 € |
| 391 | Kurt         | Hudson       | 69 301,70 € |
| 392 | Traci        | Bogisich     | 66 958,98 € |
| 393 | Margie       | Wisoky       | 73 741,48 € |
| 394 | Tonya        | Fahey        | 67 174,49 € |
| 395 | Robin        | Cummings     | 58 248,04 € |
| 396 | Ebony        | Dooley       | 95 321,75 € |
| 397 | Kerry        | Kiehn        | 62 090,55 € |
| 398 | Edmond       | Zulauf       | 71 307,08 € |
| 399 | Darrel       | Renner       | 97 531,20 € |
| 400 | Samuel       | Hintz        | 56 505,23 € |
| 401 | Milton       | Spencer      | 74 456,00 € |
| 402 | Ramona       | Kirlin       | 94 970,73 € |
| 403 | Bernice      | Wiegand      | 52 033,04 € |
| 404 | Elias        | Howe         | 97 651,27 € |
| 405 | Roberto      | Yundt        | 62 652,13 € |
| 406 | Rosemary     | Schaefer     | 68 839,52 € |
| 407 | Terry        | Haley        | 86 348,42 € |
| 408 | Sheri        | Mitchell     | 57 715,42 € |
| 409 | Perry        | King         | 61 518,62 € |
| 410 | Betty        | Botsford     | 97 322,93 € |
| 411 | Louis        | Weimann      | 60 939,34 € |
| 412 | Marshall     | Heidenreich  | 88 487,45 € |
| 413 | Lois         | Koch         | 56 886,70 € |
| 414 | Alton        | Schultz      | 87 849,82 € |
| 415 | Bryant       | Corwin       | 63 545,35 € |
| 416 | Scott        | Schinner     | 63 194,44 € |
| 417 | Karla        | Krajcik      | 78 536,72 € |
| 418 | Alfredo      | Vandervort   | 60 981,53 € |
| 419 | Wesley       | Cole         | 63 627,14 € |
| 420 | Kristie      | Hane         | 72 576,80 € |
| 421 | Jonathan     | Haag         | 67 395,58 € |
| 422 | Shawn        | Ratke        | 71 156,76 € |
| 423 | Eddie        | Metz         | 60 392,26 € |
| 424 | Frances      | Bins         | 50 298,35 € |
| 425 | Tony         | Pfeffer      | 65 389,46 € |
| 426 | Yolanda      | Schuster     | 99 616,45 € |
| 427 | Lana         | Halvorson    | 59 606,46 € |
| 428 | Alicia       | Bradtke      | 96 629,57 € |
| 429 | Amos         | Baumbach     | 70 157,76 € |
| 430 | Floyd        | Raynor       | 81 088,19 € |
| 431 | Jon          | Jenkins      | 57 446,39 € |
| 432 | Elias        | Kuphal       | 75 968,29 € |
| 433 | Pedro        | Predovic     | 79 226,86 € |
| 434 | Jessica      | Heathcote    | 61 143,89 € |
| 435 | Lindsey      | Kovacek      | 97 743,51 € |
| 436 | Tyler        | Greenfelder  | 95 764,51 € |
| 437 | Marion       | Kautzer      | 68 247,16 € |
| 438 | Janie        | Marvin       | 59 593,98 € |
| 439 | Nathan       | Barton       | 98 958,20 € |
| 440 | Celia        | Hagenes      | 55 858,97 € |
| 441 | Delbert      | Lubowitz     | 59 267,64 € |
| 442 | Kelly        | Medhurst     | 63 280,53 € |
| 443 | Ralph        | Lueilwitz    | 50 350,17 € |
| 444 | Cary         | Yost         | 96 934,71 € |
| 445 | Lonnie       | Bashirian    | 76 109,23 € |
| 446 | Claire       | Brown        | 63 015,21 € |
| 447 | Grace        | Harber       | 76 656,79 € |
| 448 | Janie        | Maggio       | 75 100,48 € |
| 449 | Lora         | Wolf         | 62 790,08 € |
| 450 | Erma         | Lindgren     | 50 992,38 € |
| 451 | Erik         | Cruickshank  | 85 137,26 € |
| 452 | Wilbur       | Grimes       | 61 844,22 € |
| 453 | Shawna       | Parisian     | 85 909,02 € |
| 454 | Cindy        | Gislason     | 55 927,69 € |
| 455 | Julio        | Beer         | 84 416,72 € |
| 456 | Carole       | Hintz        | 67 774,26 € |
| 457 | Grant        | Zieme        | 55 139,48 € |
| 458 | Benny        | Turcotte     | 77 752,90 € |
| 459 | Marty        | Predovic     | 88 693,35 € |
| 460 | Eloise       | Cartwright   | 67 841,90 € |
| 461 | Bert         | Macejkovic   | 70 948,62 € |
| 462 | Luis         | Hansen       | 57 917,28 € |
| 463 | Noah         | Schinner     | 70 205,07 € |
| 464 | Don          | Swift        | 83 846,08 € |
| 465 | Alyssa       | Pollich      | 92 025,52 € |
| 466 | Craig        | Wilderman    | 74 374,66 € |
| 467 | Andres       | Jenkins      | 68 743,52 € |
| 468 | Guy          | Lesch        | 59 731,59 € |
| 469 | Eugene       | Goldner      | 88 579,25 € |
| 470 | Lindsay      | Marks        | 56 124,81 € |
| 471 | Tanya        | Hintz        | 70 772,36 € |
| 472 | Max          | Cummerata    | 91 507,36 € |
| 473 | Patsy        | Christiansen | 86 900,25 € |
| 474 | Ruth         | Bruen        | 93 391,25 € |
| 475 | Tom          | Cole         | 60 015,88 € |
| 476 | Charlene     | Goyette      | 75 040,63 € |
| 477 | Ted          | Mann         | 77 324,64 € |
| 478 | George       | Ferry        | 86 090,05 € |
| 479 | Horace       | Stark        | 75 461,10 € |
| 480 | Sandy        | Kozey        | 61 485,46 € |
| 481 | Richard      | Hodkiewicz   | 81 577,34 € |
| 482 | Angelina     | Rutherford   | 85 489,63 € |
| 483 | Audrey       | Christiansen | 99 398,50 € |
| 484 | Ella         | Littel       | 65 535,18 € |
| 485 | Gina         | Bruen        | 50 564,33 € |
| 486 | Carolyn      | Nolan        | 69 736,17 € |
| 487 | Bernice      | Labadie      | 72 465,56 € |
| 488 | Krystal      | Purdy        | 79 207,99 € |
| 489 | Tommie       | Brakus       | 98 868,50 € |
| 490 | Bernard      | Wehner       | 93 934,24 € |
| 491 | Casey        | Terry        | 69 148,67 € |
| 492 | Connie       | Hansen       | 63 577,44 € |
| 493 | Lora         | Strosin      | 53 705,29 € |
| 494 | Grant        | Klocko       | 87 161,39 € |
| 495 | Terrance     | Monahan      | 93 972,86 € |
| 496 | Troy         | Ritchie      | 67 831,12 € |
| 497 | Deanna       | Klocko       | 69 116,80 € |
| 498 | Susie        | Casper       | 53 448,48 € |
| 499 | Deanna       | Greenholt    | 62 398,17 € |

- First
- Prev
- 1
- 1
- Next
- Last

0 - 0 of 0 items

0 items

ODataQuery

```
@using Blazorise.DataGrid.Extensions;

<DataGrid TItem="Employee"
          Data="@employeeList"
          ReadData="@OnReadData"
          TotalItems="@totalEmployees"
          PageSize="10"
          ShowPager
          Responsive>
    <DataGridCommandColumn />
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
    <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
    <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable>
        <EditTemplate>
            <NumericEdit TValue="decimal" Value="@((decimal)context.CellValue)" ValueChanged="@( v => context.CellValue = v)" />
        </EditTemplate>
    </DataGridColumn>
</DataGrid>

<Row>
    <Column>
        <Card>
            <CardHeader>
                ODataQuery
            </CardHeader>
            <CardBody>
                <Code>@oDataQuery</Code>
            </CardBody>
        </Card>
    </Column>
</Row>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private string oDataQuery;
    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    private int totalEmployees;

    private async Task OnReadData( DataGridReadDataEventArgs<Employee> e )
    {
        oDataQuery = e.ToODataString( "https://services.odata.org/V4/Northwind/Northwind.svc/Employees" );

        if ( !e.CancellationToken.IsCancellationRequested )
        {
            List<Employee> response = null;

            // this can be call to anything, in this case we're calling a fictional api
            //var response = await Http.GetJsonAsync<Employee[]>( $"some-api/employees?page={e.Page}&pageSize={e.PageSize}" );
            if ( e.ReadDataMode is DataGridReadDataMode.Virtualize )
                response = ( await EmployeeData.GetDataAsync() ).Skip( e.VirtualizeOffset ).Take( e.VirtualizeCount ).ToList();
            else if ( e.ReadDataMode is DataGridReadDataMode.Paging )
                response = ( await EmployeeData.GetDataAsync() ).Skip( ( e.Page - 1 ) * e.PageSize ).Take( e.PageSize ).ToList();
            else
                throw new Exception( "Unhandled ReadDataMode" );

            if ( !e.CancellationToken.IsCancellationRequested )
            {
                totalEmployees = ( await EmployeeData.GetDataAsync() ).Count;
                employeeList = new List<Employee>( response ); // an actual data for the current page
            }
        }
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 