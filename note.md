=IF(C2<>"", LEFT(C2, FIND(",", C2) - 1), "")

<!DOCTYPE html>
<html>

<head>
    <title>Sales Market Survey</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
    <!-- <link rel="stylesheet" href="https://unicons.iconscout.com/release/v4.0.0/css/line.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/select2/4.1.0/css/select2.min.css"> -->
</head>

<body>
    <h1>Sales Market Survey</h1>
    <form id="submit-to-google-sheet">
        <label for="name">Customer name:</label>
        <input type="text" id="name" name="Customer Name" required>

        <label for="streetAddress">Street address:</label>
        <input type="text" id="streetAddress" name="streetAddress" required>

        <label for="state">State:</label>
        <select id="state" name="State" onchange="populateCities()">
            <option value="">Choose State</option>
            <option value="Punjab">Punjab</option>
            <option value="Sindh">Sindh</option>
            <option value="Khyber Pakhtunkhwa">Khyber Pakhtunkhwa</option>
            <option value="Balochistan">Balochistan</option>
            <option value="Islamabad Capital Territory">Islamabad Capital Territory</option>
            <option value="Gilgit-Baltistan (formerly known as the Northern Areas)">Gilgit-Baltistan (formerly known as
                the Northern Areas)</option>
            <option value="Azad Jammu and Kashmir">Azad Jammu and Kashmir</option>
        </select>

        <label for="city">City:</label>
        <select id="city" name="City">
            <option value="">Select a City</option>
        </select>

        <!-- Rest of the form fields -->

        <input type="submit" value="Submit">
    </form>

    <script>
        // City data based on selected state
        const cityData = {
            Punjab: ["Burewala", "Vehari", "Lahore"],
            Sindh: ["Karachi"],
            "Khyber Pakhtunkhwa": ["Peshawar", "Abbottabad"],
            Balochistan: ["Quetta"],
            "Islamabad Capital Territory": ["Islamabad"],
            "Gilgit-Baltistan (formerly known as the Northern Areas)": ["Gilgit", "Skardu"],
            "Azad Jammu and Kashmir": ["Muzaffarabad"]
        };

        function populateCities() {
            const stateSelect = document.getElementById("state");
            const citySelect = document.getElementById("city");
            const selectedState = stateSelect.value;

            // Clear existing options
            citySelect.innerHTML = '<option value="">Select a City</option>';

            // Populate with cities based on selected state
            if (selectedState && cityData[selectedState]) {
                const cities = cityData[selectedState];
                for (const city of cities) {
                    const option = document.createElement("option");
                    option.value = city;
                    option.text = city;
                    citySelect.appendChild(option);
                }
            }
        }

        const scriptURL = 'https://script.google.com/macros/s/AKfycbw2stZCG20-egcwu1Ltyzs1kfshvbNgbJc8bFNJhdvGZ9r9hCxSlGFblzKWM52UBhcW/exec';
        const form = document.getElementById("submit-to-google-sheet");

        form.addEventListener('submit', e => {
            e.preventDefault();
            fetch(scriptURL, { method: 'POST', body: new FormData(form) })
                .then(response => alert('Success!', response))
                .catch(error => alert('Error!', error.message));
        });
    </script>

</body>

</html>

> how to disallow negative value

> cities list
>
> > Punjab

"Abdul Hakim",
"Ahmadpur East",
"Ahmedpur East",
"Arifwala",
"Attock",
"Attock Khurd",
"Bagu Na Mohra",
"Bahawalnagar",
"Bahawalpur",
"Basla",
"Bhakkar",
"Bhalwal",
"Bhawana",
"Burewala",
"Cantonment",
"Chakwal",
"Chauk Azam",
"Chenab Nagar",
"Chiniot",
"Chishtian",
"Chunian",
"Daska",
"Dera Ghazi Khan",
"Dipalpur",
"Faisalabad",
"Gojra",
"Gujranwala",
"Gujrat",
"Hafizabad",
"Harunabad",
"Hasilpur",
"Hassan Abdal",
"Hujra Shah Muqim",
"Jalalpur Jattan",
"Jaranwala",
"Jauharabad",
"Jhang",
"Jhang City",
"Jhelum",
"Kabirwala",
"Kahror Pakka",
"Kamalia",
"Kasur",
"Khanewal",
"Khanpur",
"Kharian",
"Khushab",
"Kot Addu",
"Kundian",
"Lahore",
"Lala Musa",
"Lalian",
"Layyah",
"Lodhran",
"Mandi Bahauddin",
"Mandi Burewala",
"Mian Channu",
"Mian Channun",
"Mianwali",
"Multan",
"Muridke",
"Murree",
"Muzaffargarh",
"Nankana Sahib",
"Narowal",
"Nurkot",
"Okara",
"Pakpattan",
"Pasrur",
"Pattoki",
"Qaboola",
"Rahim Yar Khan",
"Rahimyar Khan",
"Raiwind",
"Rajanpur",
"Rangewala",
"Rawalpindi",
"Saddiqabad",
"Sahiwal",
"Sambrial",
"Samundri",
"Sarai Alamgir",
"Sargodha",
"Shakargarh",
"Shekhupura",
"Shujaabad",
"Sialkot",
"Sialkot City",
"Talagang",
"Taxila",
"Toba Tek Singh",
"Vehari",
"Vihari",
"Wah Cantonment",
"Wahga",
"Zafarwal",

> > Sindh

"Badin",
"Bulri Shah Karim",
"Chuhar Jamali",
"Dadu",
"Darya Khan Marri",
"Daulatpur",
"Dokri",
"Ghotki",
"Goth Tando Sumro",
"Hala",
"Hyderabad",
"Hyderabad City",
"Jacobabad",
"Jamshoro",
"Kambar",
"Kandhkot",
"Kandiaro",
"Karachi",
"Kashmore",
"Kathri",
"Khairpur",
"Khairpur Mir’s",
"Kotri",
"Larkana",
"Matiari",
"Mian Sahib",
"Mirpur Bathoro",
"Mirpur Khas",
"Mithi",
"Moro",
"Naushahro Firoz",
"Nawabshah",
"Ratodero",
"Rohri",
"Sanghar",
"Sann",
"Sehwan",
"Shah Latif Town",
"Shahdadkot",
"Shikarpur",
"Sinjhor",
"Sita Road",
"Sujawal",
"Sukkur",
"Tando Allahyar",
"Tando Muhammad Khan",
"Thari Mirwah",
"Thatta",
"Umerkot",

> > Khyber Pakhtunkhwa

"Abbottabad",
"Alpur",
"Baffa",
"Bahrain",
"Bannu",
"Bara",
"Bat Khela",
"Batgram",
"Batkhela",
"Buner",
"Charsadda",
"Chitral",
"Daggar",
"Darra Adam Khel",
"Dera Ismail Khan",
"Gadoon Amazai",
"Hangu",
"Haripur",
"Jamrud",
"Karak",
"Kohat",
"Kohistan",
"Kulachi",
"Lakki Marwat",
"Landi Kotal",
"Lower Dir",
"Malakand",
"Mansehra",
"Mardan",
"Masho Khel",
"Mingaora",
"Mingora",
"Nowshera",
"Parachinar",
"Peshawar",
"Risalpur",
"Risalpur Cantonment",
"Saidu Sharif",
"Shabqadar",
"Shangla",
"Swabi",
"Swat",
"Takht-i-Bahi",
"Tank",
"Timargara",
"Timergara",
"Upper Dir"

> > Balochistan

Quetta
Gwadar
Turbat
Chaman
Sibi
Zhob
Pishin
Khuzdar
Hub
Dera Murad Jamali
Usta Muhammad
Nushki
Mastung
Kalat
Kharan
Panjgur
Washuk
Pasni
Awaran
Kech
Lasbela
Qila Saifullah
Ziarat
Loralai
Duki
Chagai
Qila Abdullah
Dalbandin
Harnai
Dera Bugti
Kohlu
Barkhan
Naseerabad
Jaffarabad
Sohbatpu

> > Gilgit-Baltistan

"Aliabad",
"Askole",
"Astore",
"Bunji",
"Chilas",
"Dainyor",
"Danyor",
"Darel",
"Gahkuch",
"Gakuch",
"Ganish",
"Ghanche",
"Ghizer",
"Gilgit",
"Gupis",
"Haramosh",
"Hundur",
"Hunza",
"Hussainabad",
"Jalalabad",
"Kargah",
"Karimabad",
"Khaplu",
"Kharmang",
"Nagar",
"Phander",
"Rattu",
"Rondu",
"Shigar",
"Skardu",
"Sust",
"Tangi",
"Thaleem",
"Tolti",
"Yasin Valley"

> > Azad Jammu and Kashmir

"Muzaffarabad",
"Mirpur",
"Kotli",
"Bhimber",
"Rawalakot",
"Bagh",
"Pallandri",
"Hajira",
"Sudhanoti",
"Haveli",
"Athmuqam",
"Abbaspur",
"Forward Kahuta",
"Garhi Dupatta",
"Neelum",
"Hattian Bala",
"Charhoi",
"Chikar",
"Dhirkot",
"Sehnsa",
"Khui Ratta",
"Samahni",
"Khuiratta",
"Nakyal",
"Trarkhel",
"Mandol",
"Mirpur Mathelo",
"Mangla",
"New Mirpur",
"Chakswari",
"Naukot",
"Palandri",
"Palangi",
"Ponch",
"Rara",
"Samani",
"Sharda"

<!-- Google sheet script -->

var sheetName = 'SalesMarketSurvey';
var scriptProp = PropertiesService.getScriptProperties();
var recipientEmail = 'muzaffarrafiq1717@gmail.com'; // Specify the email address to which the notification should be sent

function intialSetupSurvey() {
var activeSpreadsheet = SpreadsheetApp.getActiveSpreadsheet();
scriptProp.setProperty('key', activeSpreadsheet.getId());
}

function doPost(e) {
var lock = LockService.getScriptLock();
lock.tryLock(10000);

try {
var doc = SpreadsheetApp.openById(scriptProp.getProperty('key'));
var sheet = doc.getSheetByName(sheetName);

    var headers = sheet.getRange(1, 1, 1, sheet.getLastColumn()).getValues()[0];
    var nextRow = sheet.getLastRow() + 1;

    var newRow = headers.map(function(header) {
      return header === 'timestamp' ? new Date() : e.parameter[header];
    });

    sheet.getRange(nextRow, 1, 1, newRow.length).setValues([newRow]);

    // Send email notification
    var subject = 'New row added in Google Sheets (Sales Market Survey)';
    var message = 'A new row has been added in the sheet: ' + sheetName + '\n\n';
    message += 'Row: ' + nextRow + '\n';
    message += 'Column values: ' + newRow.join(', ');

    MailApp.sendEmail(recipientEmail, subject, message);

    return ContentService
      .createTextOutput(JSON.stringify({ 'result': 'success', 'row': nextRow }))
      .setMimeType(ContentService.MimeType.JSON);

} catch (e) {
return ContentService
.createTextOutput(JSON.stringify({ 'result': 'error', 'error': e }))
.setMimeType(ContentService.MimeType.JSON);
} finally {
lock.releaseLock();
}
}

<!-- end of Google sheet script -->

Abdul Hakim
Ahmadpur East
Ahmedpur East
Arifwala
Attock
Attock Khurd
Bagu Na Mohra
Bahawalnagar
Bahawalpur
Basla
Bhakkar
Bhalwal
Bhawana
Burewala
Cantonment
Chakwal
Chauk Azam
Chenab Nagar
Chiniot
Chishtian
Chunian
Daska
Dera Ghazi Khan
Dipalpur
Faisalabad
Gojra
Gujranwala
Gujrat
Hafizabad
Harunabad
Hasilpur
Hassan Abdal
Hujra Shah Muqim
Jalalpur Jattan
Jaranwala
Jauharabad
Jhang
Jhang City
Jhelum
Kabirwala
Kahror Pakka
Kamalia
Kasur
Khanewal
Khanpur
Kharian
Khushab
Kot Addu
Kundian
Lahore
Lala Musa
Lalian
Layyah
Lodhran
Mandi Bahauddin
Mandi Burewala
Mian Channu
Mian Channun
Mianwali
Multan
Muridke
Murree
Muzaffargarh
Nankana Sahib
Narowal
Nurkot
Okara
Pakpattan
Pasrur
Pattoki
Qaboola
Rahim Yar Khan
Rahimyar Khan
Raiwind
Rajanpur
Rangewala
Rawalpindi
Saddiqabad
Sahiwal
Sambrial
Samundri
Sarai Alamgir
Sargodha
Shakargarh
Shekhupura
Shujaabad
Sialkot
Sialkot City
Talagang
Taxila
Toba Tek Singh
Vehari
Vihari
Wah Cantonment
Wahga
Zafarwal
],
Sindh: ["Badin",
"Bulri Shah Karim",
"Chuhar Jamali",
"Dadu",
"Darya Khan Marri",
"Daulatpur",
"Dokri",
"Ghotki",
"Goth Tando Sumro",
"Hala",
"Hyderabad",
"Hyderabad City",
"Jacobabad",
"Jamshoro",
"Kambar",
"Kandhkot",
"Kandiaro",
"Karachi",
"Kashmore",
"Kathri",
"Khairpur",
"Khairpur Mir",
"Kotri",
"Larkana",
"Matiari",
"Mian Sahib",
"Mirpur Bathoro",
"Mirpur Khas",
"Mithi",
"Moro",
"Naushahro Firoz",
"Nawabshah",
"Ratodero",
"Rohri",
"Sanghar",
"Sann",
"Sehwan",
"Shah Latif Town",
"Shahdadkot",
"Shikarpur",
"Sinjhor",
"Sita Road",
"Sujawal",
"Sukkur",
"Tando Allahyar",
"Tando Muhammad Khan",
"Thari Mirwah",
"Thatta",
"Umerkot"],
"Khyber Pakhtunkhwa": ["Abbottabad",
"Alpur",
"Baffa",
"Bahrain",
"Bannu",
"Bara",
"Bat Khela",
"Batgram",
"Batkhela",
"Buner",
"Charsadda",
"Chitral",
"Daggar",
"Darra Adam Khel",
"Dera Ismail Khan",
"Gadoon Amazai",
"Hangu",
"Haripur",
"Jamrud",
"Karak",
"Kohat",
"Kohistan",
"Kulachi",
"Lakki Marwat",
"Landi Kotal",
"Lower Dir",
"Malakand",
"Mansehra",
"Mardan",
"Masho Khel",
"Mingaora",
"Mingora",
"Nowshera",
"Parachinar",
"Peshawar",
"Risalpur",
"Risalpur Cantonment",
"Saidu Sharif",
"Shabqadar",
"Shangla",
"Swabi",
"Swat",
"Takht-i-Bahi",
"Tank",
"Timargara",
"Timergara",
"Upper Dir"],
Balochistan: ["Quetta",
"Gwadar",
"Turbat",
"Chaman",
"Sibi",
"Zhob",
"Pishin",
"Khuzdar",
"Hub",
"Dera Murad Jamali",
"Usta Muhammad",
"Nushki",
"Mastung",
"Kalat",
"Kharan",
"Panjgur",
"Washuk",
"Pasni",
"Awaran",
"Kech",
"Lasbela",
"Qila Saifullah",
"Ziarat",
"Loralai",
"Duki",
"Chagai",
"Qila Abdullah",
"Dalbandin",
"Harnai",
"Dera Bugti",
"Kohlu",
"Barkhan",
"Naseerabad",
"Jaffarabad",
"Sohbatpur"],
"Islamabad Capital Territory": ["Islamabad", "Murree"],
"Gilgit-Baltistan (formerly known as the Northern Areas)": ["Aliabad",
"Askole",
"Astore",
"Bunji",
"Chilas",
"Dainyor",
"Danyor",
"Darel",
"Gahkuch",
"Gakuch",
"Ganish",
"Ghanche",
"Ghizer",
"Gilgit",
"Gupis",
"Haramosh",
"Hundur",
"Hunza",
"Hussainabad",
"Jalalabad",
"Kargah",
"Karimabad",
"Khaplu",
"Kharmang",
"Nagar",
"Phander",
"Rattu",
"Rondu",
"Shigar",
"Skardu",
"Sust",
"Tangi",
"Thaleem",
"Tolti",
"Yasin Valley"],
"Azad Jammu and Kashmir": ["Muzaffarabad",
"Mirpur",
"Kotli",
"Bhimber",
"Rawalakot",
"Bagh",
"Pallandri",
"Hajira",
"Sudhanoti",
"Haveli",
"Athmuqam",
"Abbaspur",
"Forward Kahuta",
"Garhi Dupatta",
"Neelum",
"Hattian Bala",
"Charhoi",
"Chikar",
"Dhirkot",
"Sehnsa",
"Khui Ratta",
"Samahni",
"Khuiratta",
"Nakyal",
"Trarkhel",
"Mandol",
"Mirpur Mathelo",
"Mangla",
"New Mirpur",
"Chakswari",
"Naukot",
"Palandri",
"Palangi",
"Ponch",
"Rara",
"Samani",
"Sharda"

                 


                 function sendEmailAndMoveRow() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var recipientAddress = ss.getSheetByName('recipientAddress');
  var notificationMessage = ss.getSheetByName('notificationMessage');
   var sourceSheet1 = ss.getSheetByName('JMRefrigerationForm');
  var sourceSheet2 = ss.getSheetByName('EnergyFuelConsumptionData');
  var sourceSheet3 = ss.getSheetByName('JMsteamBoilerForm');
  var sourceSheet4 = ss.getSheetByName('JMUtilityForm');
  var backupSheet = ss.getSheetByName('MasterSheet');

  var subject = notificationMessage.getRange(2, 1).getValue();
  var message = notificationMessage.getRange(2, 2).getValue();
  var n = recipientAddress.getLastRow();

  for (var i = 2; i <= n; i++) {
    var emailAddress = recipientAddress.getRange(i, 1).getValue();
    MailApp.sendEmail(emailAddress, subject, message);
  }

  var lastRow1 = sourceSheet1.getLastRow();
  var lastRow2 = sourceSheet2.getLastRow();
  var lastRow3 = sourceSheet3.getLastRow();
  var lastRow4 = sourceSheet4.getLastRow();

  var lastRowValues1 = sourceSheet1.getRange(lastRow1, 1, 1, sourceSheet1.getLastColumn()).getValues();
  var lastRowValues2 = sourceSheet2.getRange(lastRow2, 1, 1, sourceSheet2.getLastColumn()).getValues();
  var lastRowValues3 = sourceSheet3.getRange(lastRow3, 1, 1, sourceSheet3.getLastColumn()).getValues();
  var lastRowValues4 = sourceSheet4.getRange(lastRow4, 1, 1, sourceSheet4.getLastColumn()).getValues();

  var mergedValues = lastRowValues1.concat(lastRowValues2, lastRowValues3, lastRowValues4);

  var destinationRow = getDestinationRow(backupSheet, mergedValues[0][0]);

  backupSheet.insertRowBefore(destinationRow);
  backupSheet.getRange(destinationRow, 1, 1, mergedValues[0].length).setValues(mergedValues);

  sourceSheet1.deleteRow(lastRow1);
  sourceSheet2.deleteRow(lastRow2);
  sourceSheet3.deleteRow(lastRow3);
  sourceSheet4.deleteRow(lastRow4);
}

function getDestinationRow(sheet, heading) {
  var headings = sheet.getRange(1, 1, 1, sheet.getLastColumn()).getValues()[0];
  var headingIndex = headings.indexOf(heading);

  if (headingIndex !== -1) {
    return sheet.getLastRow() + 1;
  }

  return headings.filter(Boolean).length + 2;
}
