# Blazorise DataGrid: Aggregates

Show aggregate values in the footer of the grid.

## Overview

The DataGrid provider several built-in aggregates for column values. Supported aggregate functions are:

Sum Calculate total(sum) value of the collection.
Average Calculates the average of the numeric items in the collection.
Min Finds the smallest value in the collection.
Max Finds the largest value in the collection.
Count Counts the elements in a collection.
TrueCount Counts boolean elements with true value.
FalseCount Counts boolean elements with false value.

## Examples

### Aggregates

DataGrid will automatically generate necessary group cells based on the defined  options.

| #   | First Name   | Last Name   | Email                       | Salary          |
|-----|--------------|-------------|-----------------------------|-----------------|
| 1   | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 €     |
| 2   | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 €     |
| 3   | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 €     |
| 4   | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 €     |
| 5   | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 €     |
| 6   | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 €     |
| 7   | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 €     |
| 8   | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 €     |
| 9   | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 €     |
| 10  | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 €     |
|     |              |             | Total emails: 499           | 36 847 614,76 € |

### Large Data

By default all aggregate operations are run on in-memory . When working with large datasets that is not possible. So just as in the previous examples for large datasets you need to work with  and set the  property.

| #   | First Name   | Last Name    | Email                              | Salary      |
|-----|--------------|--------------|------------------------------------|-------------|
| 1   | Samuel       | Collier      | Samuel.Collier62@gmail.com         | 86 030,41 € |
| 2   | Irvin        | Ziemann      | Irvin.Ziemann@gmail.com            | 61 781,31 € |
| 3   | Gerald       | Pollich      | Gerald82@yahoo.com                 | 58 810,75 € |
| 4   | Cora         | Conn         | Cora27@yahoo.com                   | 84 414,66 € |
| 5   | Alfonso      | D'Amore      | Alfonso.DAmore@hotmail.com         | 69 318,29 € |
| 6   | Jessie       | Wilkinson    | Jessie_Wilkinson@gmail.com         | 78 566,12 € |
| 7   | Gregory      | Renner       | Gregory63@hotmail.com              | 57 456,82 € |
| 8   | Maryann      | Hilpert      | Maryann.Hilpert12@gmail.com        | 89 153,38 € |
| 9   | Merle        | Pacocha      | Merle3@gmail.com                   | 55 349,94 € |
| 10  | Angelina     | Ward         | Angelina42@gmail.com               | 73 625,86 € |
| 11  | Kara         | Brekke       | Kara.Brekke@hotmail.com            | 58 321,87 € |
| 12  | Yvette       | Ferry        | Yvette22@gmail.com                 | 89 658,90 € |
| 13  | Pablo        | Friesen      | Pablo_Friesen96@gmail.com          | 77 090,27 € |
| 14  | Ernest       | Homenick     | Ernest_Homenick92@yahoo.com        | 54 910,14 € |
| 15  | Leslie       | Wehner       | Leslie_Wehner@hotmail.com          | 78 930,58 € |
| 16  | Miguel       | Lynch        | Miguel.Lynch0@gmail.com            | 65 348,06 € |
| 17  | Tommy        | Swaniawski   | Tommy_Swaniawski@gmail.com         | 92 326,27 € |
| 18  | Viola        | Wilderman    | Viola.Wilderman@yahoo.com          | 76 575,00 € |
| 19  | Brenda       | Jacobson     | Brenda_Jacobson55@gmail.com        | 86 145,68 € |
| 20  | Roger        | Herzog       | Roger_Herzog@gmail.com             | 53 168,45 € |
| 21  | Casey        | Weber        | Casey90@yahoo.com                  | 56 257,49 € |
| 22  | Tara         | Schoen       | Tara_Schoen@yahoo.com              | 72 637,29 € |
| 23  | Al           | Sanford      | Al_Sanford1@yahoo.com              | 88 870,12 € |
| 24  | Jill         | Stokes       | Jill.Stokes@yahoo.com              | 59 252,89 € |
| 25  | Marian       | Armstrong    | Marian_Armstrong@yahoo.com         | 69 182,74 € |
| 26  | Janie        | Stanton      | Janie26@yahoo.com                  | 51 608,79 € |
| 27  | Dixie        | Block        | Dixie65@yahoo.com                  | 89 653,26 € |
| 28  | Teresa       | Dietrich     | Teresa.Dietrich@yahoo.com          | 56 151,34 € |
| 29  | Renee        | Herzog       | Renee39@yahoo.com                  | 93 592,47 € |
| 30  | Damon        | Lubowitz     | Damon_Lubowitz@hotmail.com         | 89 271,37 € |
| 31  | Cody         | Rau          | Cody56@hotmail.com                 | 63 067,69 € |
| 32  | Ethel        | Kassulke     | Ethel.Kassulke@yahoo.com           | 92 175,30 € |
| 33  | Rudy         | Walsh        | Rudy_Walsh54@gmail.com             | 76 356,17 € |
| 34  | Ross         | Hauck        | Ross18@hotmail.com                 | 51 620,31 € |
| 35  | Otis         | Little       | Otis_Little28@hotmail.com          | 77 906,94 € |
| 36  | Benjamin     | Friesen      | Benjamin40@yahoo.com               | 78 343,54 € |
| 37  | Moses        | Mosciski     | Moses_Mosciski@gmail.com           | 99 202,48 € |
| 38  | Kellie       | Murazik      | Kellie_Murazik@gmail.com           | 98 314,89 € |
| 39  | Nichole      | Keebler      | Nichole69@gmail.com                | 65 412,00 € |
| 40  | Bobbie       | Rogahn       | Bobbie.Rogahn7@yahoo.com           | 52 889,16 € |
| 41  | Charlie      | Borer        | Charlie.Borer68@hotmail.com        | 50 448,59 € |
| 42  | Luis         | Rutherford   | Luis.Rutherford@hotmail.com        | 83 594,06 € |
| 43  | Jared        | Pfannerstill | Jared82@gmail.com                  | 54 282,76 € |
| 44  | Floyd        | Satterfield  | Floyd96@yahoo.com                  | 59 157,17 € |
| 45  | Claude       | Parker       | Claude_Parker55@gmail.com          | 58 576,97 € |
| 46  | Donald       | Daugherty    | Donald.Daugherty@gmail.com         | 66 692,86 € |
| 47  | Roland       | Bruen        | Roland5@yahoo.com                  | 98 404,23 € |
| 48  | Pauline      | Conroy       | Pauline_Conroy@yahoo.com           | 69 674,96 € |
| 49  | Lora         | Lockman      | Lora55@hotmail.com                 | 74 035,99 € |
| 50  | Joey         | Koelpin      | Joey_Koelpin@yahoo.com             | 57 184,86 € |
| 51  | Stacey       | Graham       | Stacey_Graham88@gmail.com          | 88 562,39 € |
| 52  | Daisy        | Medhurst     | Daisy75@yahoo.com                  | 51 011,13 € |
| 53  | Erin         | Corwin       | Erin_Corwin17@gmail.com            | 70 013,81 € |
| 54  | Arturo       | Denesik      | Arturo.Denesik@gmail.com           | 61 456,56 € |
| 55  | Cheryl       | Collier      | Cheryl.Collier@yahoo.com           | 59 868,88 € |
| 56  | Andres       | Williamson   | Andres34@yahoo.com                 | 74 180,71 € |
| 57  | Phyllis      | Wilderman    | Phyllis.Wilderman90@gmail.com      | 59 518,29 € |
| 58  | Billy        | Wiza         | Billy84@gmail.com                  | 92 241,90 € |
| 59  | Woodrow      | Gibson       | Woodrow_Gibson55@yahoo.com         | 90 288,10 € |
| 60  | Cristina     | Harris       | Cristina.Harris@yahoo.com          | 81 762,53 € |
| 61  | Darlene      | Daniel       | Darlene.Daniel52@gmail.com         | 74 142,55 € |
| 62  | Courtney     | Frami        | Courtney.Frami@yahoo.com           | 68 435,70 € |
| 63  | Mae          | Feeney       | Mae92@gmail.com                    | 65 623,26 € |
| 64  | Josh         | Doyle        | Josh75@yahoo.com                   | 87 057,60 € |
| 65  | Gwen         | Abbott       | Gwen.Abbott86@yahoo.com            | 65 189,89 € |
| 66  | Mona         | Beier        | Mona8@gmail.com                    | 80 367,71 € |
| 67  | Minnie       | Corwin       | Minnie_Corwin96@yahoo.com          | 78 002,56 € |
| 68  | Dwight       | Runolfsson   | Dwight99@gmail.com                 | 73 986,40 € |
| 69  | Beth         | Bartell      | Beth.Bartell@yahoo.com             | 85 841,65 € |
| 70  | Steve        | Schulist     | Steve_Schulist@hotmail.com         | 94 190,45 € |
| 71  | Pam          | Greenholt    | Pam44@gmail.com                    | 75 695,28 € |
| 72  | Darrel       | Williamson   | Darrel_Williamson@yahoo.com        | 70 327,72 € |
| 73  | Rolando      | Sauer        | Rolando_Sauer@hotmail.com          | 84 971,22 € |
| 74  | Cesar        | Schaefer     | Cesar79@yahoo.com                  | 92 704,04 € |
| 75  | Luis         | Leannon      | Luis13@gmail.com                   | 61 167,01 € |
| 76  | Fannie       | Williamson   | Fannie_Williamson@gmail.com        | 94 194,50 € |
| 77  | Marianne     | Pouros       | Marianne_Pouros60@hotmail.com      | 71 394,54 € |
| 78  | Spencer      | Rogahn       | Spencer.Rogahn12@gmail.com         | 55 993,84 € |
| 79  | Donnie       | Luettgen     | Donnie_Luettgen@hotmail.com        | 77 655,38 € |
| 80  | Blanca       | Breitenberg  | Blanca77@hotmail.com               | 75 633,97 € |
| 81  | Pat          | Rohan        | Pat_Rohan@gmail.com                | 50 151,72 € |
| 82  | Virginia     | Kassulke     | Virginia_Kassulke@yahoo.com        | 77 411,81 € |
| 83  | Lela         | Breitenberg  | Lela_Breitenberg44@hotmail.com     | 53 894,64 € |
| 84  | Randal       | Koss         | Randal.Koss67@hotmail.com          | 93 602,37 € |
| 85  | Kimberly     | Christiansen | Kimberly_Christiansen2@hotmail.com | 65 089,52 € |
| 86  | Jean         | Boyer        | Jean42@hotmail.com                 | 99 805,01 € |
| 87  | Muriel       | Shields      | Muriel.Shields12@gmail.com         | 66 809,95 € |
| 88  | Marcus       | Emmerich     | Marcus_Emmerich@yahoo.com          | 99 401,27 € |
| 89  | Faith        | Nicolas      | Faith.Nicolas@yahoo.com            | 50 439,25 € |
| 90  | Boyd         | Davis        | Boyd_Davis@gmail.com               | 58 591,48 € |
| 91  | Wilbur       | Stiedemann   | Wilbur29@gmail.com                 | 64 479,16 € |
| 92  | Roberto      | Stracke      | Roberto_Stracke@yahoo.com          | 57 007,18 € |
| 93  | Mindy        | Smitham      | Mindy.Smitham5@hotmail.com         | 56 810,55 € |
| 94  | Dianne       | Maggio       | Dianne.Maggio83@yahoo.com          | 73 990,94 € |
| 95  | Mandy        | Bahringer    | Mandy55@hotmail.com                | 69 018,94 € |
| 96  | Marlon       | Ledner       | Marlon.Ledner26@hotmail.com        | 72 372,09 € |
| 97  | Laverne      | Schuster     | Laverne.Schuster38@gmail.com       | 84 767,07 € |
| 98  | Kendra       | Corkery      | Kendra_Corkery@gmail.com           | 79 303,18 € |
| 99  | Chris        | Barton       | Chris.Barton@yahoo.com             | 68 642,57 € |
| 100 | Ed           | Price        | Ed.Price21@gmail.com               | 84 665,20 € |
| 101 | Tracey       | Durgan       | Tracey.Durgan3@hotmail.com         | 63 539,54 € |
| 102 | Alyssa       | Gaylord      | Alyssa95@gmail.com                 | 92 963,65 € |
| 103 | Helen        | Mueller      | Helen_Mueller@gmail.com            | 51 704,43 € |
| 104 | Ronald       | Moen         | Ronald56@yahoo.com                 | 88 173,43 € |
| 105 | Gerard       | McDermott    | Gerard.McDermott@gmail.com         | 79 616,46 € |
| 106 | Samantha     | Zboncak      | Samantha_Zboncak@gmail.com         | 75 298,13 € |
| 107 | Van          | Gleichner    | Van.Gleichner99@hotmail.com        | 90 917,71 € |
| 108 | Frederick    | Bode         | Frederick.Bode44@gmail.com         | 52 949,98 € |
| 109 | Lela         | Gutmann      | Lela85@gmail.com                   | 52 247,22 € |
| 110 | Harvey       | Gutmann      | Harvey_Gutmann85@gmail.com         | 82 998,73 € |
| 111 | Luis         | Robel        | Luis.Robel21@gmail.com             | 91 952,69 € |
| 112 | Brandi       | Ward         | Brandi_Ward@yahoo.com              | 70 341,50 € |
| 113 | Margie       | Hills        | Margie16@hotmail.com               | 93 092,75 € |
| 114 | Toby         | Beatty       | Toby19@gmail.com                   | 66 829,50 € |
| 115 | Bobby        | Ward         | Bobby.Ward@gmail.com               | 82 475,01 € |
| 116 | Jason        | Barrows      | Jason.Barrows@gmail.com            | 87 777,57 € |
| 117 | Francis      | Ullrich      | Francis26@gmail.com                | 69 615,22 € |
| 118 | Herman       | Marquardt    | Herman.Marquardt51@yahoo.com       | 84 744,26 € |
| 119 | Francis      | Gleason      | Francis.Gleason35@hotmail.com      | 58 666,45 € |
| 120 | Carolyn      | Kunze        | Carolyn_Kunze68@hotmail.com        | 80 404,42 € |
| 121 | Terry        | Rogahn       | Terry_Rogahn62@gmail.com           | 69 352,10 € |
| 122 | Kendra       | Senger       | Kendra.Senger26@gmail.com          | 93 641,61 € |
| 123 | Rochelle     | Kessler      | Rochelle.Kessler@yahoo.com         | 96 931,95 € |
| 124 | Yvonne       | Halvorson    | Yvonne63@hotmail.com               | 94 598,15 € |
| 125 | Kendra       | Bernhard     | Kendra_Bernhard86@hotmail.com      | 59 931,41 € |
| 126 | Katherine    | Price        | Katherine.Price22@hotmail.com      | 60 998,60 € |
| 127 | Lillian      | Wyman        | Lillian_Wyman@yahoo.com            | 52 545,83 € |
| 128 | Velma        | Wunsch       | Velma_Wunsch@yahoo.com             | 74 742,06 € |
| 129 | Kristy       | Herman       | Kristy.Herman@yahoo.com            | 96 811,63 € |
| 130 | Erick        | Parker       | Erick15@gmail.com                  | 88 902,23 € |
| 131 | Dean         | Johnston     | Dean.Johnston26@hotmail.com        | 72 987,32 € |
| 132 | Phillip      | Brekke       | Phillip.Brekke91@hotmail.com       | 69 227,78 € |
| 133 | Ashley       | Blick        | Ashley32@hotmail.com               | 74 736,25 € |
| 134 | Larry        | Feeney       | Larry42@hotmail.com                | 76 448,86 € |
| 135 | Kayla        | Glover       | Kayla.Glover@gmail.com             | 97 369,33 € |
| 136 | Alvin        | Simonis      | Alvin.Simonis@gmail.com            | 62 546,08 € |
| 137 | Kevin        | Kassulke     | Kevin74@hotmail.com                | 80 076,32 € |
| 138 | Teresa       | O'Kon        | Teresa.OKon40@yahoo.com            | 87 065,63 € |
| 139 | Ella         | Cartwright   | Ella.Cartwright51@yahoo.com        | 90 099,49 € |
| 140 | Albert       | Howe         | Albert.Howe7@gmail.com             | 50 647,80 € |
| 141 | Andrew       | Pfeffer      | Andrew35@yahoo.com                 | 99 691,54 € |
| 142 | Garrett      | Jenkins      | Garrett_Jenkins47@gmail.com        | 56 963,04 € |
| 143 | Louis        | Kuvalis      | Louis.Kuvalis96@hotmail.com        | 80 519,61 € |
| 144 | Myrtle       | Tromp        | Myrtle_Tromp@gmail.com             | 69 930,94 € |
| 145 | Andrew       | Murphy       | Andrew_Murphy42@gmail.com          | 55 579,15 € |
| 146 | Patricia     | Gaylord      | Patricia47@gmail.com               | 89 805,17 € |
| 147 | Preston      | Kuvalis      | Preston_Kuvalis3@hotmail.com       | 83 615,78 € |
| 148 | Merle        | Osinski      | Merle4@yahoo.com                   | 92 220,65 € |
| 149 | Alberto      | Bernhard     | Alberto.Bernhard41@gmail.com       | 52 655,29 € |
| 150 | Darrell      | Beatty       | Darrell51@hotmail.com              | 54 224,58 € |
| 151 | Joanne       | Bartoletti   | Joanne.Bartoletti3@yahoo.com       | 53 083,34 € |
| 152 | Gloria       | Bahringer    | Gloria93@gmail.com                 | 65 360,79 € |
| 153 | Cameron      | Hane         | Cameron_Hane76@gmail.com           | 74 440,82 € |
| 154 | Conrad       | Dooley       | Conrad77@hotmail.com               | 79 099,12 € |
| 155 | Erik         | Marks        | Erik0@yahoo.com                    | 93 408,43 € |
| 156 | Carolyn      | Wolff        | Carolyn2@hotmail.com               | 97 583,81 € |
| 157 | Silvia       | O'Hara       | Silvia78@gmail.com                 | 72 185,23 € |
| 158 | Dexter       | Hettinger    | Dexter_Hettinger@yahoo.com         | 90 261,40 € |
| 159 | Margaret     | Ledner       | Margaret.Ledner38@yahoo.com        | 62 783,44 € |
| 160 | Ellis        | Herzog       | Ellis.Herzog4@gmail.com            | 60 940,26 € |
| 161 | Merle        | Bahringer    | Merle.Bahringer92@hotmail.com      | 53 660,05 € |
| 162 | Roberto      | Yost         | Roberto.Yost48@hotmail.com         | 61 169,10 € |
| 163 | Stacy        | Kuhlman      | Stacy98@yahoo.com                  | 93 823,76 € |
| 164 | Corey        | Monahan      | Corey_Monahan35@gmail.com          | 57 966,22 € |
| 165 | Chelsea      | Sawayn       | Chelsea_Sawayn51@yahoo.com         | 52 049,90 € |
| 166 | Clifton      | Mills        | Clifton_Mills@gmail.com            | 68 356,52 € |
| 167 | Teri         | Kling        | Teri.Kling29@yahoo.com             | 67 176,87 € |
| 168 | Tanya        | Farrell      | Tanya8@hotmail.com                 | 58 393,52 € |
| 169 | Marianne     | Carroll      | Marianne.Carroll@yahoo.com         | 92 390,80 € |
| 170 | Rosalie      | Purdy        | Rosalie.Purdy19@gmail.com          | 86 463,78 € |
| 171 | Shirley      | Greenfelder  | Shirley_Greenfelder2@hotmail.com   | 91 685,68 € |
| 172 | Delores      | Steuber      | Delores.Steuber50@hotmail.com      | 94 113,92 € |
| 173 | Terri        | Klein        | Terri.Klein96@hotmail.com          | 68 647,08 € |
| 174 | Marjorie     | Beahan       | Marjorie_Beahan75@hotmail.com      | 84 706,53 € |
| 175 | Reginald     | Reinger      | Reginald_Reinger31@hotmail.com     | 85 323,79 € |
| 176 | Kelley       | Bode         | Kelley.Bode39@gmail.com            | 79 071,76 € |
| 177 | Loren        | Howell       | Loren_Howell74@gmail.com           | 93 204,93 € |
| 178 | Lindsey      | Smith        | Lindsey_Smith76@yahoo.com          | 99 085,43 € |
| 179 | Doug         | Wilkinson    | Doug_Wilkinson41@yahoo.com         | 79 267,68 € |
| 180 | Bernadette   | Watsica      | Bernadette18@gmail.com             | 77 302,18 € |
| 181 | Billy        | Volkman      | Billy93@gmail.com                  | 68 235,94 € |
| 182 | Courtney     | Reinger      | Courtney59@yahoo.com               | 54 541,73 € |
| 183 | Marjorie     | Dietrich     | Marjorie_Dietrich@yahoo.com        | 51 211,89 € |
| 184 | Meghan       | Pollich      | Meghan71@gmail.com                 | 62 102,58 € |
| 185 | Phillip      | Smitham      | Phillip_Smitham40@yahoo.com        | 79 097,74 € |
| 186 | Verna        | Klocko       | Verna.Klocko@gmail.com             | 66 963,02 € |
| 187 | Rodolfo      | Mertz        | Rodolfo95@hotmail.com              | 57 742,48 € |
| 188 | Sabrina      | Hyatt        | Sabrina.Hyatt0@yahoo.com           | 82 874,64 € |
| 189 | Roger        | Lehner       | Roger.Lehner20@gmail.com           | 85 927,11 € |
| 190 | Julia        | Huels        | Julia35@gmail.com                  | 67 309,00 € |
| 191 | May          | Reynolds     | May52@yahoo.com                    | 96 990,64 € |
| 192 | Bennie       | Williamson   | Bennie_Williamson@yahoo.com        | 67 591,28 € |
| 193 | Evan         | Okuneva      | Evan_Okuneva65@gmail.com           | 79 220,93 € |
| 194 | Diana        | Rohan        | Diana.Rohan@gmail.com              | 78 141,34 € |
| 195 | Shari        | Smitham      | Shari99@gmail.com                  | 60 195,83 € |
| 196 | Ella         | Schiller     | Ella_Schiller94@gmail.com          | 83 482,98 € |
| 197 | Karen        | Towne        | Karen_Towne54@hotmail.com          | 54 088,60 € |
| 198 | Kelly        | Jones        | Kelly.Jones46@gmail.com            | 78 290,86 € |
| 199 | Robin        | Lesch        | Robin.Lesch@gmail.com              | 66 805,27 € |
| 200 | Guy          | Mayert       | Guy.Mayert25@gmail.com             | 68 127,67 € |
| 201 | Misty        | Ondricka     | Misty.Ondricka33@yahoo.com         | 75 954,94 € |
| 202 | Julius       | White        | Julius43@gmail.com                 | 78 706,96 € |
| 203 | Josh         | Gaylord      | Josh_Gaylord48@hotmail.com         | 60 487,10 € |
| 204 | Debra        | Johnston     | Debra.Johnston@gmail.com           | 83 953,91 € |
| 205 | Kellie       | Marks        | Kellie35@yahoo.com                 | 64 800,44 € |
| 206 | Taylor       | Goodwin      | Taylor37@hotmail.com               | 83 261,10 € |
| 207 | Lee          | Metz         | Lee58@gmail.com                    | 98 403,81 € |
| 208 | Eddie        | Murazik      | Eddie36@hotmail.com                | 68 029,89 € |
| 209 | Ernesto      | McLaughlin   | Ernesto_McLaughlin60@gmail.com     | 99 436,01 € |
| 210 | Laurence     | Turner       | Laurence_Turner87@gmail.com        | 51 909,85 € |
| 211 | Hazel        | Vandervort   | Hazel74@gmail.com                  | 94 267,75 € |
| 212 | Cecelia      | Nader        | Cecelia.Nader@gmail.com            | 74 472,40 € |
| 213 | Phil         | Ledner       | Phil_Ledner@yahoo.com              | 68 881,51 € |
| 214 | Krystal      | Metz         | Krystal.Metz@gmail.com             | 83 250,52 € |
| 215 | Don          | Altenwerth   | Don.Altenwerth32@gmail.com         | 52 897,75 € |
| 216 | Candace      | McCullough   | Candace69@hotmail.com              | 96 247,14 € |
| 217 | Sabrina      | Gulgowski    | Sabrina.Gulgowski68@gmail.com      | 50 276,69 € |
| 218 | Laurence     | Batz         | Laurence3@yahoo.com                | 64 410,12 € |
| 219 | Shane        | Rippin       | Shane.Rippin@hotmail.com           | 75 551,08 € |
| 220 | Bernadette   | Morissette   | Bernadette98@hotmail.com           | 98 512,13 € |
| 221 | Alexander    | West         | Alexander_West@gmail.com           | 61 698,25 € |
| 222 | Stella       | McKenzie     | Stella.McKenzie@yahoo.com          | 78 466,06 € |
| 223 | Arlene       | Parker       | Arlene.Parker62@yahoo.com          | 57 641,64 € |
| 224 | Brett        | Durgan       | Brett14@hotmail.com                | 67 162,65 € |
| 225 | Muriel       | Tremblay     | Muriel.Tremblay@yahoo.com          | 78 588,45 € |
| 226 | Adam         | Upton        | Adam_Upton60@yahoo.com             | 88 672,89 € |
| 227 | Lester       | Bartell      | Lester_Bartell@gmail.com           | 59 093,66 € |
| 228 | Cristina     | Streich      | Cristina54@gmail.com               | 81 916,04 € |
| 229 | Ernestine    | Heathcote    | Ernestine.Heathcote31@yahoo.com    | 71 069,20 € |
| 230 | Clarence     | Emard        | Clarence_Emard67@gmail.com         | 82 071,65 € |
| 231 | Mona         | Kertzmann    | Mona4@hotmail.com                  | 56 353,15 € |
| 232 | Tracey       | Pfeffer      | Tracey_Pfeffer@gmail.com           | 91 484,81 € |
| 233 | Tony         | Hartmann     | Tony_Hartmann93@yahoo.com          | 80 992,77 € |
| 234 | Harry        | Treutel      | Harry.Treutel@hotmail.com          | 51 423,99 € |
| 235 | Ervin        | Tillman      | Ervin_Tillman17@yahoo.com          | 82 561,69 € |
| 236 | Derek        | Schoen       | Derek.Schoen79@hotmail.com         | 95 956,53 € |
| 237 | Anthony      | Price        | Anthony.Price62@gmail.com          | 74 884,58 € |
| 238 | Shari        | Zboncak      | Shari_Zboncak@gmail.com            | 96 737,83 € |
| 239 | Glenn        | Leannon      | Glenn_Leannon50@gmail.com          | 63 534,18 € |
| 240 | Guy          | Treutel      | Guy_Treutel@gmail.com              | 60 108,71 € |
| 241 | Angie        | Hoppe        | Angie_Hoppe@hotmail.com            | 65 635,04 € |
| 242 | Catherine    | Bartell      | Catherine98@yahoo.com              | 98 196,01 € |
| 243 | Timmy        | Torp         | Timmy_Torp0@yahoo.com              | 54 958,10 € |
| 244 | Walter       | Schimmel     | Walter_Schimmel94@hotmail.com      | 51 050,65 € |
| 245 | Cecilia      | Lakin        | Cecilia32@yahoo.com                | 95 127,62 € |
| 246 | Colin        | Reichel      | Colin17@yahoo.com                  | 66 112,87 € |
| 247 | Victoria     | Deckow       | Victoria.Deckow@gmail.com          | 60 492,50 € |
| 248 | Homer        | Cormier      | Homer19@hotmail.com                | 90 229,04 € |
| 249 | Spencer      | O'Reilly     | Spencer34@yahoo.com                | 60 243,52 € |
| 250 | Allan        | Hand         | Allan.Hand@gmail.com               | 59 170,08 € |
| 251 | Cameron      | Ondricka     | Cameron.Ondricka@gmail.com         | 79 858,60 € |
| 252 | Mark         | Bins         | Mark.Bins@hotmail.com              | 52 790,83 € |
| 253 | Jaime        | Jacobson     | Jaime_Jacobson@yahoo.com           | 76 493,75 € |
| 254 | Irma         | Watsica      | Irma_Watsica10@yahoo.com           | 58 546,05 € |
| 255 | Shaun        | Braun        | Shaun83@gmail.com                  | 59 642,92 € |
| 256 | Diana        | Effertz      | Diana83@gmail.com                  | 82 583,67 € |
| 257 | Steven       | Dooley       | Steven_Dooley@yahoo.com            | 64 657,62 € |
| 258 | Irma         | Kovacek      | Irma.Kovacek@hotmail.com           | 94 208,96 € |
| 259 | Emmett       | Herzog       | Emmett_Herzog@yahoo.com            | 67 817,81 € |
| 260 | Kelly        | Davis        | Kelly_Davis@yahoo.com              | 71 400,98 € |
| 261 | Luz          | Morar        | Luz24@gmail.com                    | 64 577,48 € |
| 262 | Marta        | Harris       | Marta.Harris@gmail.com             | 66 971,72 € |
| 263 | Mabel        | Wolff        | Mabel_Wolff@gmail.com              | 74 724,96 € |
| 264 | Samuel       | Gutkowski    | Samuel_Gutkowski50@gmail.com       | 60 034,46 € |
| 265 | Emma         | Emmerich     | Emma.Emmerich39@hotmail.com        | 72 648,66 € |
| 266 | Irvin        | Mitchell     | Irvin_Mitchell@yahoo.com           | 50 003,10 € |
| 267 | Nicolas      | Halvorson    | Nicolas.Halvorson@hotmail.com      | 71 526,27 € |
| 268 | Charlie      | Jerde        | Charlie3@gmail.com                 | 73 030,99 € |
| 269 | Ramona       | Dibbert      | Ramona_Dibbert81@hotmail.com       | 74 358,11 € |
| 270 | Clifton      | Klein        | Clifton_Klein@gmail.com            | 97 270,09 € |
| 271 | Stella       | Steuber      | Stella_Steuber25@gmail.com         | 59 692,64 € |
| 272 | Juanita      | Champlin     | Juanita.Champlin@yahoo.com         | 72 780,75 € |
| 273 | Isaac        | Stamm        | Isaac.Stamm96@hotmail.com          | 69 292,97 € |
| 274 | Doyle        | Schumm       | Doyle63@gmail.com                  | 51 427,45 € |
| 275 | Clay         | Grimes       | Clay20@gmail.com                   | 51 772,08 € |
| 276 | Roland       | Mayert       | Roland_Mayert6@hotmail.com         | 81 883,80 € |
| 277 | Edmond       | Bahringer    | Edmond.Bahringer16@hotmail.com     | 50 929,17 € |
| 278 | Randall      | Daniel       | Randall.Daniel@gmail.com           | 89 905,30 € |
| 279 | Gregory      | Spencer      | Gregory.Spencer31@hotmail.com      | 74 161,60 € |
| 280 | Owen         | Swaniawski   | Owen5@yahoo.com                    | 95 707,25 € |
| 281 | Laverne      | Pacocha      | Laverne_Pacocha5@yahoo.com         | 65 789,34 € |
| 282 | Sara         | Shields      | Sara.Shields@yahoo.com             | 86 180,98 € |
| 283 | Christian    | Hoeger       | Christian.Hoeger13@gmail.com       | 71 363,32 € |
| 284 | Damon        | Denesik      | Damon.Denesik22@hotmail.com        | 55 400,84 € |
| 285 | Marjorie     | Emmerich     | Marjorie.Emmerich@yahoo.com        | 63 652,59 € |
| 286 | Tasha        | Borer        | Tasha57@gmail.com                  | 94 186,62 € |
| 287 | Joseph       | Kris         | Joseph16@hotmail.com               | 67 814,68 € |
| 288 | Bethany      | Beer         | Bethany_Beer@yahoo.com             | 65 998,18 € |
| 289 | Terrance     | Thiel        | Terrance.Thiel@yahoo.com           | 80 137,01 € |
| 290 | Bob          | Casper       | Bob_Casper31@yahoo.com             | 68 748,43 € |
| 291 | Joe          | Lakin        | Joe_Lakin@yahoo.com                | 98 278,19 € |
| 292 | Lee          | Wolff        | Lee_Wolff13@gmail.com              | 94 738,69 € |
| 293 | Alvin        | Smith        | Alvin.Smith@gmail.com              | 68 593,23 € |
| 294 | Jimmie       | Dietrich     | Jimmie_Dietrich49@yahoo.com        | 84 267,88 € |
| 295 | Tyrone       | Dach         | Tyrone_Dach86@gmail.com            | 94 728,32 € |
| 296 | Van          | Mills        | Van.Mills@hotmail.com              | 60 109,47 € |
| 297 | Ted          | Gibson       | Ted.Gibson8@gmail.com              | 65 825,81 € |
| 298 | Roxanne      | Kuhn         | Roxanne_Kuhn@hotmail.com           | 79 023,74 € |
| 299 | Regina       | Keeling      | Regina41@gmail.com                 | 66 369,94 € |
| 300 | Helen        | Witting      | Helen.Witting@yahoo.com            | 74 575,87 € |
| 301 | Oliver       | Daniel       | Oliver.Daniel0@hotmail.com         | 54 641,11 € |
| 302 | Doug         | Leannon      | Doug.Leannon77@yahoo.com           | 76 076,55 € |
| 303 | Carol        | Schmeler     | Carol49@hotmail.com                | 83 833,88 € |
| 304 | Don          | Mills        | Don9@gmail.com                     | 53 632,72 € |
| 305 | Lindsey      | Considine    | Lindsey_Considine@gmail.com        | 98 571,25 € |
| 306 | Grace        | Nader        | Grace.Nader18@gmail.com            | 82 399,49 € |
| 307 | Candice      | Rodriguez    | Candice_Rodriguez2@yahoo.com       | 90 887,74 € |
| 308 | Lula         | Schultz      | Lula_Schultz27@hotmail.com         | 97 039,29 € |
| 309 | Lee          | Bins         | Lee_Bins@gmail.com                 | 71 842,44 € |
| 310 | Saul         | Howe         | Saul5@yahoo.com                    | 52 676,35 € |
| 311 | Louise       | Gislason     | Louise.Gislason@yahoo.com          | 88 305,26 € |
| 312 | Myrtle       | Hackett      | Myrtle.Hackett3@gmail.com          | 68 996,49 € |
| 313 | Casey        | Zemlak       | Casey.Zemlak71@yahoo.com           | 57 259,51 € |
| 314 | Kristen      | Huel         | Kristen.Huel@gmail.com             | 54 689,50 € |
| 315 | Krista       | Kris         | Krista_Kris@hotmail.com            | 93 758,65 € |
| 316 | Danielle     | Jerde        | Danielle_Jerde10@gmail.com         | 99 301,40 € |
| 317 | Angelica     | Tremblay     | Angelica.Tremblay70@yahoo.com      | 85 313,90 € |
| 318 | Louise       | Abshire      | Louise69@gmail.com                 | 77 784,92 € |
| 319 | Wm           | Bogisich     | Wm35@hotmail.com                   | 62 126,09 € |
| 320 | Maryann      | Wisoky       | Maryann.Wisoky78@yahoo.com         | 85 135,69 € |
| 321 | Betsy        | Wisozk       | Betsy.Wisozk@gmail.com             | 77 627,62 € |
| 322 | Alexander    | Stoltenberg  | Alexander_Stoltenberg@gmail.com    | 99 611,36 € |
| 323 | Judith       | Flatley      | Judith.Flatley@hotmail.com         | 77 310,19 € |
| 324 | Stewart      | Treutel      | Stewart_Treutel@gmail.com          | 50 889,65 € |
| 325 | Helen        | Schiller     | Helen.Schiller83@yahoo.com         | 73 442,69 € |
| 326 | Heidi        | Haag         | Heidi_Haag@yahoo.com               | 51 397,29 € |
| 327 | Ross         | Thiel        | Ross.Thiel58@hotmail.com           | 92 754,54 € |
| 328 | Amanda       | Senger       | Amanda.Senger@hotmail.com          | 89 441,31 € |
| 329 | Beth         | Hilpert      | Beth.Hilpert48@hotmail.com         | 62 114,78 € |
| 330 | Curtis       | Hessel       | Curtis.Hessel@yahoo.com            | 57 498,77 € |
| 331 | Alma         | Gibson       | Alma_Gibson37@hotmail.com          | 90 762,65 € |
| 332 | Jeannette    | Schaden      | Jeannette.Schaden97@yahoo.com      | 96 075,03 € |
| 333 | Roberto      | Herman       | Roberto.Herman@hotmail.com         | 97 894,29 € |
| 334 | Clarence     | Blanda       | Clarence_Blanda@hotmail.com        | 50 450,45 € |
| 335 | Jeffery      | Kassulke     | Jeffery_Kassulke97@hotmail.com     | 55 046,88 € |
| 336 | Trevor       | Schuppe      | Trevor.Schuppe@hotmail.com         | 80 338,20 € |
| 337 | Ron          | Lebsack      | Ron_Lebsack24@gmail.com            | 55 184,82 € |
| 338 | Cedric       | Auer         | Cedric_Auer@gmail.com              | 67 321,90 € |
| 339 | Gina         | Schiller     | Gina.Schiller@gmail.com            | 89 055,19 € |
| 340 | Julius       | Schmidt      | Julius.Schmidt29@gmail.com         | 69 183,31 € |
| 341 | Brandi       | Corkery      | Brandi84@yahoo.com                 | 67 152,53 € |
| 342 | Alicia       | McClure      | Alicia47@yahoo.com                 | 93 251,90 € |
| 343 | Michele      | Waters       | Michele.Waters93@gmail.com         | 92 624,38 € |
| 344 | Kristen      | Hoeger       | Kristen89@yahoo.com                | 60 848,20 € |
| 345 | Kate         | Heathcote    | Kate.Heathcote@yahoo.com           | 62 751,58 € |
| 346 | Rudolph      | Leffler      | Rudolph.Leffler@gmail.com          | 90 085,95 € |
| 347 | Garry        | McCullough   | Garry.McCullough81@gmail.com       | 87 440,86 € |
| 348 | Tracey       | Rutherford   | Tracey.Rutherford77@hotmail.com    | 71 584,47 € |
| 349 | Shelly       | Bartoletti   | Shelly_Bartoletti@hotmail.com      | 95 964,97 € |
| 350 | Johnny       | Padberg      | Johnny79@gmail.com                 | 91 804,24 € |
| 351 | David        | Smitham      | David.Smitham34@hotmail.com        | 68 092,90 € |
| 352 | Priscilla    | Conroy       | Priscilla_Conroy@hotmail.com       | 92 922,27 € |
| 353 | Shannon      | Emard        | Shannon37@hotmail.com              | 53 804,17 € |
| 354 | Paula        | Kautzer      | Paula73@hotmail.com                | 53 365,86 € |
| 355 | Jay          | Douglas      | Jay.Douglas93@yahoo.com            | 62 473,03 € |
| 356 | Wesley       | Torphy       | Wesley.Torphy7@gmail.com           | 54 390,81 € |
| 357 | Lorraine     | Williamson   | Lorraine.Williamson@hotmail.com    | 80 333,70 € |
| 358 | Johanna      | Hahn         | Johanna97@hotmail.com              | 55 954,42 € |
| 359 | Alexander    | Mertz        | Alexander4@gmail.com               | 99 571,59 € |
| 360 | Wilson       | Bruen        | Wilson1@gmail.com                  | 64 776,40 € |
| 361 | Hubert       | Pfannerstill | Hubert14@hotmail.com               | 63 008,59 € |
| 362 | Alan         | O'Kon        | Alan23@hotmail.com                 | 80 885,59 € |
| 363 | Willie       | Metz         | Willie1@yahoo.com                  | 51 930,24 € |
| 364 | Joey         | Ferry        | Joey.Ferry@hotmail.com             | 94 608,69 € |
| 365 | Ricky        | Hermann      | Ricky.Hermann@gmail.com            | 83 772,49 € |
| 366 | Devin        | Stamm        | Devin47@yahoo.com                  | 94 867,24 € |
| 367 | Joshua       | Homenick     | Joshua_Homenick14@gmail.com        | 76 817,11 € |
| 368 | Larry        | Daugherty    | Larry_Daugherty@hotmail.com        | 73 207,94 € |
| 369 | Claude       | Gleason      | Claude_Gleason66@hotmail.com       | 85 370,52 € |
| 370 | Sammy        | Murazik      | Sammy.Murazik@yahoo.com            | 69 384,89 € |
| 371 | Angelina     | Abshire      | Angelina76@yahoo.com               | 60 717,13 € |
| 372 | Tasha        | Kunze        | Tasha_Kunze@gmail.com              | 64 904,36 € |
| 373 | Lula         | Collier      | Lula_Collier@gmail.com             | 90 212,24 € |
| 374 | Deanna       | Stiedemann   | Deanna.Stiedemann@yahoo.com        | 78 268,35 € |
| 375 | Shelley      | Johns        | Shelley_Johns@gmail.com            | 87 217,90 € |
| 376 | Albert       | Little       | Albert97@yahoo.com                 | 81 290,85 € |
| 377 | Carlos       | Reichel      | Carlos68@yahoo.com                 | 98 138,19 € |
| 378 | Ebony        | Schiller     | Ebony22@yahoo.com                  | 68 048,74 € |
| 379 | Andrew       | Schultz      | Andrew_Schultz@gmail.com           | 60 699,23 € |
| 380 | Ebony        | Strosin      | Ebony_Strosin67@gmail.com          | 62 514,96 € |
| 381 | Janet        | Hauck        | Janet_Hauck@hotmail.com            | 84 912,58 € |
| 382 | Darryl       | Barton       | Darryl.Barton@gmail.com            | 52 279,26 € |
| 383 | Lawrence     | Reilly       | Lawrence.Reilly@hotmail.com        | 69 375,45 € |
| 384 | Merle        | Abbott       | Merle.Abbott@hotmail.com           | 68 595,59 € |
| 385 | Hugo         | O'Conner     | Hugo_OConner@yahoo.com             | 83 359,23 € |
| 386 | Janice       | Rodriguez    | Janice65@gmail.com                 | 80 747,25 € |
| 387 | Sabrina      | Rohan        | Sabrina.Rohan@gmail.com            | 87 173,33 € |
| 388 | Carrie       | Rutherford   | Carrie.Rutherford@hotmail.com      | 60 272,93 € |
| 389 | Dexter       | Mayert       | Dexter_Mayert@yahoo.com            | 76 548,50 € |
| 390 | Neil         | Collier      | Neil92@gmail.com                   | 65 578,63 € |
| 391 | Kurt         | Hudson       | Kurt_Hudson@hotmail.com            | 69 301,70 € |
| 392 | Traci        | Bogisich     | Traci.Bogisich@yahoo.com           | 66 958,98 € |
| 393 | Margie       | Wisoky       | Margie_Wisoky21@hotmail.com        | 73 741,48 € |
| 394 | Tonya        | Fahey        | Tonya_Fahey@gmail.com              | 67 174,49 € |
| 395 | Robin        | Cummings     | Robin_Cummings18@hotmail.com       | 58 248,04 € |
| 396 | Ebony        | Dooley       | Ebony.Dooley@yahoo.com             | 95 321,75 € |
| 397 | Kerry        | Kiehn        | Kerry_Kiehn@hotmail.com            | 62 090,55 € |
| 398 | Edmond       | Zulauf       | Edmond.Zulauf7@hotmail.com         | 71 307,08 € |
| 399 | Darrel       | Renner       | Darrel64@yahoo.com                 | 97 531,20 € |
| 400 | Samuel       | Hintz        | Samuel_Hintz59@yahoo.com           | 56 505,23 € |
| 401 | Milton       | Spencer      | Milton.Spencer59@yahoo.com         | 74 456,00 € |
| 402 | Ramona       | Kirlin       | Ramona.Kirlin5@hotmail.com         | 94 970,73 € |
| 403 | Bernice      | Wiegand      | Bernice48@yahoo.com                | 52 033,04 € |
| 404 | Elias        | Howe         | Elias.Howe0@yahoo.com              | 97 651,27 € |
| 405 | Roberto      | Yundt        | Roberto.Yundt6@gmail.com           | 62 652,13 € |
| 406 | Rosemary     | Schaefer     | Rosemary_Schaefer30@yahoo.com      | 68 839,52 € |
| 407 | Terry        | Haley        | Terry.Haley@hotmail.com            | 86 348,42 € |
| 408 | Sheri        | Mitchell     | Sheri0@hotmail.com                 | 57 715,42 € |
| 409 | Perry        | King         | Perry_King@yahoo.com               | 61 518,62 € |
| 410 | Betty        | Botsford     | Betty80@gmail.com                  | 97 322,93 € |
| 411 | Louis        | Weimann      | Louis85@gmail.com                  | 60 939,34 € |
| 412 | Marshall     | Heidenreich  | Marshall_Heidenreich@yahoo.com     | 88 487,45 € |
| 413 | Lois         | Koch         | Lois.Koch@yahoo.com                | 56 886,70 € |
| 414 | Alton        | Schultz      | Alton.Schultz16@yahoo.com          | 87 849,82 € |
| 415 | Bryant       | Corwin       | Bryant_Corwin@yahoo.com            | 63 545,35 € |
| 416 | Scott        | Schinner     | Scott_Schinner@gmail.com           | 63 194,44 € |
| 417 | Karla        | Krajcik      | Karla.Krajcik@yahoo.com            | 78 536,72 € |
| 418 | Alfredo      | Vandervort   | Alfredo4@yahoo.com                 | 60 981,53 € |
| 419 | Wesley       | Cole         | Wesley97@gmail.com                 | 63 627,14 € |
| 420 | Kristie      | Hane         | Kristie.Hane28@hotmail.com         | 72 576,80 € |
| 421 | Jonathan     | Haag         | Jonathan_Haag@yahoo.com            | 67 395,58 € |
| 422 | Shawn        | Ratke        | Shawn.Ratke88@gmail.com            | 71 156,76 € |
| 423 | Eddie        | Metz         | Eddie81@gmail.com                  | 60 392,26 € |
| 424 | Frances      | Bins         | Frances_Bins@gmail.com             | 50 298,35 € |
| 425 | Tony         | Pfeffer      | Tony_Pfeffer23@yahoo.com           | 65 389,46 € |
| 426 | Yolanda      | Schuster     | Yolanda.Schuster@gmail.com         | 99 616,45 € |
| 427 | Lana         | Halvorson    | Lana34@yahoo.com                   | 59 606,46 € |
| 428 | Alicia       | Bradtke      | Alicia_Bradtke@gmail.com           | 96 629,57 € |
| 429 | Amos         | Baumbach     | Amos.Baumbach68@gmail.com          | 70 157,76 € |
| 430 | Floyd        | Raynor       | Floyd.Raynor@hotmail.com           | 81 088,19 € |
| 431 | Jon          | Jenkins      | Jon.Jenkins37@gmail.com            | 57 446,39 € |
| 432 | Elias        | Kuphal       | Elias.Kuphal47@gmail.com           | 75 968,29 € |
| 433 | Pedro        | Predovic     | Pedro_Predovic97@gmail.com         | 79 226,86 € |
| 434 | Jessica      | Heathcote    | Jessica_Heathcote72@gmail.com      | 61 143,89 € |
| 435 | Lindsey      | Kovacek      | Lindsey.Kovacek6@gmail.com         | 97 743,51 € |
| 436 | Tyler        | Greenfelder  | Tyler15@gmail.com                  | 95 764,51 € |
| 437 | Marion       | Kautzer      | Marion.Kautzer98@yahoo.com         | 68 247,16 € |
| 438 | Janie        | Marvin       | Janie.Marvin@hotmail.com           | 59 593,98 € |
| 439 | Nathan       | Barton       | Nathan_Barton61@hotmail.com        | 98 958,20 € |
| 440 | Celia        | Hagenes      | Celia5@yahoo.com                   | 55 858,97 € |
| 441 | Delbert      | Lubowitz     | Delbert66@yahoo.com                | 59 267,64 € |
| 442 | Kelly        | Medhurst     | Kelly.Medhurst21@yahoo.com         | 63 280,53 € |
| 443 | Ralph        | Lueilwitz    | Ralph95@gmail.com                  | 50 350,17 € |
| 444 | Cary         | Yost         | Cary52@yahoo.com                   | 96 934,71 € |
| 445 | Lonnie       | Bashirian    | Lonnie_Bashirian@gmail.com         | 76 109,23 € |
| 446 | Claire       | Brown        | Claire.Brown55@gmail.com           | 63 015,21 € |
| 447 | Grace        | Harber       | Grace.Harber@hotmail.com           | 76 656,79 € |
| 448 | Janie        | Maggio       | Janie.Maggio@hotmail.com           | 75 100,48 € |
| 449 | Lora         | Wolf         | Lora_Wolf@yahoo.com                | 62 790,08 € |
| 450 | Erma         | Lindgren     | Erma67@gmail.com                   | 50 992,38 € |
| 451 | Erik         | Cruickshank  | Erik6@yahoo.com                    | 85 137,26 € |
| 452 | Wilbur       | Grimes       | Wilbur2@hotmail.com                | 61 844,22 € |
| 453 | Shawna       | Parisian     | Shawna.Parisian@gmail.com          | 85 909,02 € |
| 454 | Cindy        | Gislason     | Cindy8@yahoo.com                   | 55 927,69 € |
| 455 | Julio        | Beer         | Julio.Beer70@gmail.com             | 84 416,72 € |
| 456 | Carole       | Hintz        | Carole.Hintz12@yahoo.com           | 67 774,26 € |
| 457 | Grant        | Zieme        | Grant.Zieme25@yahoo.com            | 55 139,48 € |
| 458 | Benny        | Turcotte     | Benny.Turcotte57@hotmail.com       | 77 752,90 € |
| 459 | Marty        | Predovic     | Marty_Predovic33@yahoo.com         | 88 693,35 € |
| 460 | Eloise       | Cartwright   | Eloise93@hotmail.com               | 67 841,90 € |
| 461 | Bert         | Macejkovic   | Bert_Macejkovic84@hotmail.com      | 70 948,62 € |
| 462 | Luis         | Hansen       | Luis48@yahoo.com                   | 57 917,28 € |
| 463 | Noah         | Schinner     | Noah_Schinner65@gmail.com          | 70 205,07 € |
| 464 | Don          | Swift        | Don31@gmail.com                    | 83 846,08 € |
| 465 | Alyssa       | Pollich      | Alyssa.Pollich55@hotmail.com       | 92 025,52 € |
| 466 | Craig        | Wilderman    | Craig.Wilderman16@yahoo.com        | 74 374,66 € |
| 467 | Andres       | Jenkins      | Andres.Jenkins@yahoo.com           | 68 743,52 € |
| 468 | Guy          | Lesch        | Guy.Lesch65@gmail.com              | 59 731,59 € |
| 469 | Eugene       | Goldner      | Eugene22@hotmail.com               | 88 579,25 € |
| 470 | Lindsay      | Marks        | Lindsay29@gmail.com                | 56 124,81 € |
| 471 | Tanya        | Hintz        | Tanya.Hintz@yahoo.com              | 70 772,36 € |
| 472 | Max          | Cummerata    | Max.Cummerata45@gmail.com          | 91 507,36 € |
| 473 | Patsy        | Christiansen | Patsy.Christiansen58@yahoo.com     | 86 900,25 € |
| 474 | Ruth         | Bruen        | Ruth_Bruen25@gmail.com             | 93 391,25 € |
| 475 | Tom          | Cole         | Tom_Cole16@yahoo.com               | 60 015,88 € |
| 476 | Charlene     | Goyette      | Charlene5@hotmail.com              | 75 040,63 € |
| 477 | Ted          | Mann         | Ted.Mann@gmail.com                 | 77 324,64 € |
| 478 | George       | Ferry        | George_Ferry@gmail.com             | 86 090,05 € |
| 479 | Horace       | Stark        | Horace75@gmail.com                 | 75 461,10 € |
| 480 | Sandy        | Kozey        | Sandy64@gmail.com                  | 61 485,46 € |
| 481 | Richard      | Hodkiewicz   | Richard_Hodkiewicz62@gmail.com     | 81 577,34 € |
| 482 | Angelina     | Rutherford   | Angelina0@gmail.com                | 85 489,63 € |
| 483 | Audrey       | Christiansen | Audrey74@hotmail.com               | 99 398,50 € |
| 484 | Ella         | Littel       | Ella5@hotmail.com                  | 65 535,18 € |
| 485 | Gina         | Bruen        | Gina60@gmail.com                   | 50 564,33 € |
| 486 | Carolyn      | Nolan        | Carolyn.Nolan@yahoo.com            | 69 736,17 € |
| 487 | Bernice      | Labadie      | Bernice64@yahoo.com                | 72 465,56 € |
| 488 | Krystal      | Purdy        | Krystal_Purdy86@hotmail.com        | 79 207,99 € |
| 489 | Tommie       | Brakus       | Tommie.Brakus@yahoo.com            | 98 868,50 € |
| 490 | Bernard      | Wehner       | Bernard_Wehner@gmail.com           | 93 934,24 € |
| 491 | Casey        | Terry        | Casey_Terry65@gmail.com            | 69 148,67 € |
| 492 | Connie       | Hansen       | Connie.Hansen@hotmail.com          | 63 577,44 € |
| 493 | Lora         | Strosin      | Lora_Strosin@gmail.com             | 53 705,29 € |
| 494 | Grant        | Klocko       | Grant.Klocko96@yahoo.com           | 87 161,39 € |
| 495 | Terrance     | Monahan      | Terrance22@yahoo.com               | 93 972,86 € |
| 496 | Troy         | Ritchie      | Troy11@gmail.com                   | 67 831,12 € |
| 497 | Deanna       | Klocko       | Deanna_Klocko@hotmail.com          | 69 116,80 € |
| 498 | Susie        | Casper       | Susie.Casper52@yahoo.com           | 53 448,48 € |
| 499 | Deanna       | Greenholt    | Deanna_Greenholt20@hotmail.com     | 62 398,17 € |
|     |              |              | Total emails: 0                    | 0,00 €      |

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          ReadData="@OnReadData"
          TotalItems="@totalEmployees"
          AggregateData="@employeeSummary"
          Responsive>
    <DataGridAggregates>
        <DataGridAggregate Field="@nameof( Employee.Email )" Aggregate="DataGridAggregateType.Count">
            <DisplayTemplate>
                @($"Total emails: {context.Value}")
            </DisplayTemplate>
        </DataGridAggregate>
        <DataGridAggregate Field="@nameof( Employee.Salary )" Aggregate="DataGridAggregateType.Sum" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" />
        <DataGridAggregate Field="@nameof( Employee.IsActive )" Aggregate="DataGridAggregateType.TrueCount" />
    </DataGridAggregates>
    <DataGridColumns>
        <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
        <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
        <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
        <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
        <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable>
            <EditTemplate>
                <NumericEdit TValue="decimal" Value="@((decimal)context.CellValue)" ValueChanged="@( v => context.CellValue = v)" />
            </EditTemplate>
        </DataGridColumn>
    </DataGridColumns>
</DataGrid>
```

```
@code{
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    private int totalEmployees;
    private List<Employee> employeeSummary;

    private Task OnReadData( DataGridReadDataEventArgs<Employee> e )
    {
        if ( !e.CancellationToken.IsCancellationRequested )
        {
            List<Employee> response = null;

            // this can be call to anything, in this case we're calling a fictional api
            //var response = await Http.GetJsonAsync<Employee[]>( $"some-api/employees?page={e.Page}&pageSize={e.PageSize}" );
            if ( e.ReadDataMode is DataGridReadDataMode.Virtualize )
                response = employeeList.Skip( e.VirtualizeOffset ).Take( e.VirtualizeCount ).ToList();
            else if ( e.ReadDataMode is DataGridReadDataMode.Paging )
                response = employeeList.Skip( ( e.Page - 1 ) * e.PageSize ).Take( e.PageSize ).ToList();
            else
                throw new Exception( "Unhandled ReadDataMode" );


            if ( !e.CancellationToken.IsCancellationRequested )
            {
                totalEmployees = employeeList.Count;
                employeeList = new List<Employee>( response ); // an actual data for the current page
                                                               //var aggregateResponse = await Http.GetJsonAsync<Employee[]>( $"some-aggregate-api/employees" );
                employeeSummary = employeeList; //aggregateResponse.Data
            }
        }
        return Task.CompletedTask;
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 