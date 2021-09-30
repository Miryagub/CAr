#define _CRT_SECURE_NO_WARNINGS
#include <iostream>
#include <cstring>
#include <windows.h>
#include <ctime>
#include <conio.h>
#include <stdlib.h>
  
using namespace std;

//bu func mətnin rəngini dəyişir
void colourFunc(int a)
{
	SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), a);
}
// gün.ay.il formatı
void dateTime(char starttime[], char endtime[], int dd)
{
	time_t now = time(0);
	tm* ltm = localtime(&now);
	int year = 1900 + ltm->tm_year;
	int mon = 1 + ltm->tm_mon;
	int day = ltm->tm_mday;
	char convertDate[3][5];
	int temp;
	for (int j = 0; j < 3; j++)
	{
		if (j == 0)  temp = year;
		else if (j == 1) temp = mon;
		else temp = day;
		for (int i = 0; i < 5; i++)
		{
			bool goToNext = false;
			if (temp <= 0) goToNext = true;
			else
			{
				int test = temp % 10;
				convertDate[j][i] = char(test + 48);
				temp /= 10;
			}
			if (goToNext == true)
			{
				convertDate[j][i] = '\0';
				_strrev(convertDate[j]);
				break;
			}
		}
	}
	char date[11];
	strcpy_s(date, convertDate[2]);
	strcat_s(date, ".");
	strcat_s(date, convertDate[1]);
	strcat_s(date, ".");
	strcat_s(date, convertDate[0]);
	strcpy(starttime, date);
	day += dd;
	bool test = true;
	while (test == true)
	{
		bool test = false;
		if (mon == 4 || mon == 6 || mon == 9 || mon == 11)
		{
			if (day > 30)
			{
				test = true;
				day = day - 30;
				mon++;
				if (mon > 12)
				{
					mon -= 12;
					year++;
				}
			}
		}
		else if (mon == 2)
		{

			if (day > 28)
			{
				test = true;
				day = day - 28;
				mon++;
				if (mon > 12)
				{
					mon -= 12;
					year++;
				}
			}
		}
		else
		{
			if (day > 31)
			{
				test = true;
				day = day - 31;
				mon++;
				if (mon > 12)
				{
					mon -= 12;
					year++;
				}
			}
		}
		if (test == false) break;
	}
	for (int j = 0; j < 3; j++)
	{
		if (j == 0)  temp = year;
		else if (j == 1) temp = mon;
		else temp = day;
		for (int i = 0; i < 5; i++)
		{
			bool goToNext = false;
			if (temp <= 0) goToNext = true;
			else
			{
				int test = temp % 10;
				convertDate[j][i] = char(test + 48);
				temp /= 10;
			}
			if (goToNext == true)
			{
				convertDate[j][i] = '\0';
				_strrev(convertDate[j]);
				break;
			}
		}
	}
	strcpy_s(date, convertDate[2]);
	strcat_s(date, ".");
	strcat_s(date, convertDate[1]);
	strcat_s(date, ".");
	strcat_s(date, convertDate[0]);
	strcpy(endtime, date);
}
void datefunc(char starttime[])
{
	time_t now = time(0);
	tm* ltm = localtime(&now);
	int year = 1900 + ltm->tm_year;
	int mon = 1 + ltm->tm_mon;
	int day = ltm->tm_mday;
	char convertDate[3][5];
	int temp;
	for (int j = 0; j < 3; j++)
	{
		if (j == 0)  temp = year;
		else if (j == 1) temp = mon;
		else temp = day;
		for (int i = 0; i < 5; i++)
		{
			bool goToNext = false;
			if (temp <= 0) goToNext = true;
			else
			{
				int test = temp % 10;
				convertDate[j][i] = char(test + 48);
				temp /= 10;
			}
			if (goToNext == true)
			{
				convertDate[j][i] = '\0';
				_strrev(convertDate[j]);
				break;
			}
		}
	}
	char date[11];
	strcpy_s(date, convertDate[2]);
	strcat_s(date, ".");
	strcat_s(date, convertDate[1]);
	strcat_s(date, ".");
	strcat_s(date, convertDate[0]);
	strcpy(starttime, date);
}
void introduction()
{
	Sleep(1000);
	colourFunc(8);
	cout << "                    ____ _____ _____ ____     ___ _____         _                 _" << endl;
	cout << "                   / ___|_   _| ____|  _ \\   |_ _|_   _|       / \\   ___ __ _  __| | ___ _ __ ___  _   _" << endl;
	cout << "                   \\___ \\ | | |  _| | |_) |   | |  | |        / _ \\ / __/ _  |/ _  |/ _ \\ '_   _ \\| | | |" << endl;
	cout << "                    ___) || | | |___|    /    | |  | |       / ___ \\ (_| (_| | (_| |  __/ | | | | | |_| |" << endl;
	cout << "                   |____/ |_| |_____|_|      |___| |_|      /_/   \\_\\___\\__,_|\\__,_|\\___|_| |_| |_|\\__, |" << endl;
	cout << "                                                                                                   |___/" << endl;
	cout << endl << endl << endl << endl;
	colourFunc(8);
	Sleep(2000);
	cout << "           Rent a Car Application" << endl;
	 
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j <= 45; j++)
		{
			colourFunc(0);
			if (i == 1 && j == 2)
			{
				colourFunc(8);
				cout << "Program: Miryagub Mustafayev terefinden yaradilmishdir!";
			}
			if (i == 0 && j <= 41 || (i == 2 && j <= 41) || ((i == 1 && j == 0) || (i == 1 && j == 45)))
			{
				cout << char(219);
			}
		}
		cout << endl;
	}
	Sleep(2000);
}
void adminPage();
void adminControl();
void firstPage();
void addCar();
void showCarList(int n);
void editCar();
void deleteCar();
void userHomePage();
void logUser();
void createUser();
void readUserAccountList();
void homePage();
void usermenu();
void requestForCar();
void readCarList();
void requestList();
void approveContract();
void readRequestlist();
void readContractList(int n);
void showContractList();
void customerContractList();
void removeRequest();
void terminateContract();
void extendTime();
void searchContract();
void autoDeleteContract();
void exitPage(int n);
void gotoxy(short x, short y) // hər hansı bir koordinata mətn yazmaq
{
	COORD pos = { x, y };
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
}

struct Car
{
	int id;
	char mark[50];
	char model[50];
	char numberPlate[10];
	char colour[20];
	int maxSpeed;
	int dailyRent;
	int year;
	char carisrented[5];
}car, allCarr[100];

struct userInfo
{
	char name[20];
	char surname[20];
	char cardSerialnum[10];
	char mobilNumber[15];
	char login[20];
	char password[20];
}user, allUsers[100];

struct UserLogIn
{
	char login[20];
	char password[20];
}userLogIn;

struct Request
{
	char name[20];
	char surname[20];
	char cardSerialnum[10];
	char mobilNumber[15];
	char status[5];
	int id;
	int day;
	int payment;

}request, allRequest[100], deleteRequest;

struct approve
{
	int carId;
	char cardSerialnum[10];
}acceptRequest;

struct addcontract
{
	char name[20];
	char surname[20];
	char cardSerialnum[10];
	char mobilNumber[15];
	int carId;
	int day;
	int payment;
	char starttime[11];
	char endtime[11];
}contract, allContract[100], editContract;

char enter[2]; //funksiyadan funksiyaya keçmək
int m = 0; // sorğu siyahısı
int h = 0; //istifadəçi hesablarının sayı
int g = 0; //maşınların sayı
int f = 0; // müqavilələrin sayı
int u = 0; // müqavilələrin sayı (müqavilənin avtomatik silinməsi)
char today[11]; //bu gün üçün funksiya: gg.mm.yyyy
int main()
{
	autoDeleteContract();
	introduction();
	firstPage();
	return 0;
}

void adminPage()
{
	system("cls");
	while (true)
	{
		colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Yeni mashin elave edin" << endl;
		colourFunc(14); cout << "2"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Butun avtomobillerin siyahisini daxil edin" << endl;
		colourFunc(14); cout << "3"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Avtomobil melumatlarini redakte edin" << endl;
		colourFunc(14); cout << "4"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Mashini siyahidan silin" << endl;
		colourFunc(14); cout << "5"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Istek siyahisini gosterin" << endl;
		colourFunc(14); cout << "6"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Sorgunu silin" << endl;
		colourFunc(14); cout << "7"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Muqavileni tesdiq edin" << endl;
		colourFunc(14); cout << "8"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Muqavile siyahisini gosterin" << endl;
		colourFunc(14); cout << "9"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Muqavileni legv edin" << endl;
		colourFunc(14); cout << "10"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Muqavile siyahisini axtarin" << endl << endl;
		colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Exit" << endl << endl;
		colourFunc(3); cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: "; colourFunc(7);
		colourFunc(15); cin >> enter; colourFunc(7);
		system("cls");

		if (enter[0] == 8 && enter[1] == 0)
		{
			colourFunc(4); cout << endl << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin!" << endl << endl; colourFunc(7);
		}
		else if (enter[0] == '0' && enter[1] == '\0')
		{
			firstPage();
		}
		else if (enter[0] == '1' && enter[1] == '\0')
		{
			addCar();
		}
		else if (enter[0] == '2' && enter[1] == '\0')
		{
			showCarList(1);
		}
		else if (enter[0] == '3' && enter[1] == '\0')
		{
			editCar();
		}
		else if (enter[0] == '4' && enter[1] == '\0')
		{
			deleteCar();
		}
		else if (enter[0] == '5' && enter[1] == '\0')
		{
			requestList();
		}
		else if (enter[0] == '6' && enter[1] == '\0')
		{
			removeRequest();
		}
		else if (enter[0] == '7' && enter[1] == '\0')
		{
			approveContract();
		}
		else if (enter[0] == '8' && enter[1] == '\0')
		{
			showContractList();
		}
		else if (enter[0] == '9' && enter[1] == '\0')
		{
			terminateContract();
		}
		else if (enter[0] == '1' && enter[1] == '0')
		{
			searchContract();
		}
	}
}

void showCarList(int n)
{
	system("cls");
	int row = 4;
	FILE* fptr;
	fopen_s(&fptr, "Car.txt", "r");
	if (fptr == NULL)
	{
		colourFunc(12); cout << "\t\tMashinin siyahisi boshdur!" << endl << endl; colourFunc(7);
		Sleep(4000);
		if (n == 1) adminPage();
		else usermenu();
	}
	else
	{
		fclose(fptr);
		fopen_s(&fptr, "Car.txt", "r");
		if (fptr != NULL)
		{
			colourFunc(10); cout << "\n\t\t\t<<<<<<<<<<List of all cars>>>>>>>>>>"; colourFunc(14);
			gotoxy(1, 3);
			cout << "ID";
			gotoxy(10, 3);
			cout << "Mark";
			gotoxy(22, 3);
			cout << "Model";
			gotoxy(33, 3);
			cout << "Number plate";
			gotoxy(50, 3);
			cout << "Colour";
			gotoxy(60, 3);
			cout << "Max speed";
			gotoxy(71, 3);
			cout << "Kiraye haqqi";
			gotoxy(84, 3);
			cout << "Year";
			gotoxy(92, 3);
			cout << "Avtomovbil kiraye verilir?"; colourFunc(11);
			while (fscanf(fptr, "%d %s %s %s %s %d %d %d %s\n", &car.id, car.mark, car.model,
				car.numberPlate, car.colour, &car.maxSpeed, &car.dailyRent, &car.year, car.carisrented) != EOF)
			{
				gotoxy(1, row);
				cout << car.id;
				gotoxy(10, row);
				cout << car.mark;
				gotoxy(22, row);
				cout << car.model;
				gotoxy(34, row);
				cout << car.numberPlate;
				gotoxy(51, row);
				cout << car.colour;
				gotoxy(62, row);
				cout << car.maxSpeed;
				gotoxy(75, row);
				cout << car.dailyRent;
				gotoxy(84, row);
				cout << car.year;
				gotoxy(94, row);
				cout << car.carisrented;
				row++;
			}
			fclose(fptr);
		}
		colourFunc(14); cout << endl << endl << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Back" << endl << endl;
		colourFunc(3); cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: "; colourFunc(7);
		do
		{
			cin >> enter;
			if (enter[0] != '0' && enter[1] != '\0')
			{
				colourFunc(4); cout << endl << "Etmek istediyiniz emeliyyatin nomresini daxil edin "; colourFunc(7);
			}
		} while (enter[0] != '0' && enter[1] != '\0');

		if (n == 1) adminPage();
		else usermenu();
	}
}

void editCar()
{
	int id;
	int valid = 0;
	colourFunc(3); cout << "Redakte etmek istediyiniz avtomobilin id- nomresini daxil edin:"; colourFunc(7);
	cin >> id;
	FILE* fptr;
	FILE* fptr2;
	fopen_s(&fptr, "Car.txt", "r");
	fopen_s(&fptr2, "Car2.txt", "a");
	if (fptr == NULL || fptr2 == NULL)
	{
		colourFunc(4); cout << "Mashinin siyahisi boshdur!!!" << endl << endl; colourFunc(7);
		fclose(fptr2);
		exitPage(1);
	}
	if (fptr != NULL)
	{
		while (fscanf(fptr, "%d %s %s %s %s %d %d %d %s\n", &car.id, car.mark, car.model, car.numberPlate, car.colour, &car.maxSpeed, &car.dailyRent, &car.year, car.carisrented) != -1)
		{
			if (id == car.id)
			{
				colourFunc(14); cout << "ID: "; colourFunc(11); cin >> car.id;
				colourFunc(14); cout << "Mark: "; colourFunc(11); cin >> car.mark;
				colourFunc(14);	cout << "Model: "; colourFunc(11); cin >> car.model;
				colourFunc(14); cout << "Nomre nishani: "; colourFunc(11); cin >> car.numberPlate;
				colourFunc(14); cout << "Colour: "; colourFunc(11); cin >> car.colour;
				colourFunc(14); cout << "Max speed KM/Hour: "; colourFunc(11); cin >> car.maxSpeed;
				colourFunc(14); cout << "Kiraye (AZN): "; colourFunc(11); cin >> car.dailyRent;
				colourFunc(14); cout << "Year: "; colourFunc(11); cin >> car.year; colourFunc(7);
				valid = 1;
			}
			fprintf_s(fptr2, "%d %s %s %s %s %d %d %d %s\n", car.id, car.mark, car.model, car.numberPlate, car.colour, car.maxSpeed, car.dailyRent, car.year, car.carisrented);
		}
		if (valid == 0)
		{
			colourFunc(4); cout << endl << id << "Avtomobilin sayi siyahini tapmadi" << endl << endl;
			fclose(fptr);
			fclose(fptr2);
			remove("Car2.txt");
			exitPage(1);
		}
		else
		{
			fclose(fptr);
			fclose(fptr2);
			remove("Car.txt");
			rename("Car2.txt", "Car.txt");
			colourFunc(10); cout << endl << "Avtomobil haqqinda melumat ugurla deyishdirildi" << endl << endl; colourFunc(7);
			exitPage(1);
		}

	}
}

void addCar()
{

	colourFunc(14); cout << "ID: "; colourFunc(11); cin >> car.id;
	colourFunc(14); cout << "Mark: "; colourFunc(11); cin >> car.mark;
	colourFunc(14); cout << "Model: "; colourFunc(11); cin >> car.model;
	colourFunc(14); cout << "Nomre nishani: "; colourFunc(11); cin >> car.numberPlate;
	colourFunc(14); cout << "Colour: "; colourFunc(11); cin >> car.colour;
	colourFunc(14); cout << "Max speed KM/Hour: "; colourFunc(11); cin >> car.maxSpeed;
	colourFunc(14); cout << "Kiraye (AZN): "; colourFunc(11); cin >> car.dailyRent;
	colourFunc(14); cout << "Year: "; colourFunc(11); cin >> car.year;
	strcpy(car.carisrented, "No");
	FILE* fptr;
	int num = 0;
	fopen_s(&fptr, "Car.txt", "r");
	if (fptr != NULL)
	{
		int i = 0;
		while (fscanf(fptr, "%d %s %s %s %s %d %d %d %s\n", &allCarr[i].id, allCarr[i].mark, allCarr[i].model, allCarr[i].numberPlate, allCarr[i].colour, &allCarr[i].maxSpeed, &allCarr[i].dailyRent, &allCarr[i].year, allCarr[i].carisrented) != -1)
		{
			if (allCarr[i].id == car.id)
			{
				num = 1;
			}
			i++;
		}
		fclose(fptr);
	}
	if (num == 1)
	{
		colourFunc(12); cout << car.id << " Avtomobil sayi artiq siyahida var. Zehmet olmazsa bashqa nomre sinayin";
		Sleep(3000);
		system("cls");
		addCar();
	}
	fopen_s(&fptr, "Car.txt", "a");
	if (fptr != NULL)
	{
		fprintf_s(fptr, "%d %s %s %s %s %d %d %d %s\n", car.id, car.mark, car.model, car.numberPlate, car.colour, car.maxSpeed, car.dailyRent, car.year, car.carisrented);
		fclose(fptr);
	}
	colourFunc(10); cout << endl << "Yeni avtomobil ugurla elave edildi" << endl << endl;
	while (true)
	{
		colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Yeni mashin elave edin" << endl;
		colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Exit" << endl << endl;
		cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: ";
		cin >> enter;
		system("cls");
		if (enter[0] == '0' && enter[1] == '\0')adminPage();
		else if (enter[0] == '1' && enter[1] == '\0') addCar();
		else
		{
			colourFunc(12); cout << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin!!!" << endl;
		}
	}
}

void adminControl()
{
	system("cls");
	string adminUserName;
	string adminPassword;
	while (true)
	{
		colourFunc(14); cout << "Username:";
		colourFunc(11); cin >> adminUserName;
		colourFunc(14); cout << "Password:";
		colourFunc(11); cin >> adminPassword;
		if (adminUserName == "admin" && adminPassword == "admin")
		{
			system("cls");
			adminPage();
		}
		else
		{
			system("cls");
			colourFunc(12); cout << "Istifadeci adi ve ya shifre sehvdir. Zehmet olmazsa bir daha cehd edin!" << endl;
		}
	}
}

void firstPage()
{
	system("cls");
	colourFunc(11); cout << "\t\t\t" << "Rent a Car  <=======>  Home Page" << endl;
	while (true)
	{
		colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Admin Menu" << endl;
		colourFunc(14); cout << "2"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "User Menu" << endl;
		colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Exit" << endl << endl;
		colourFunc(3); cout << "Etmek istediyiniz emeloyyatin nomresini daxil edin: ";
		colourFunc(15); cin >> enter;
		if (enter[0] == '1' && enter[1] == '\0')
		{
			adminControl();
		}
		else if (enter[0] == '0' && enter[1] == '\0')
		{
			exit(1);
		}
		else if (enter[0] == '2' && enter[1] == '\0')
		{
			userHomePage();
		}
		else
		{
			system("cls");
			colourFunc(12); cout << endl << "Sechimiz sehvdir. Zehmet olmazsa bir daha cehd edin" << endl << endl;
		}
	}
}

void deleteCar()
{
	remove("Car2.txt");
	int id, value = 0;
	colourFunc(3); cout << "Silmek istediyiniz avtomobilin id- nomresini daxil edin:";
	colourFunc(15); cin >> id;
	FILE* fptr;
	FILE* fptr2;
	fopen_s(&fptr, "Car.txt", "r");
	fopen_s(&fptr2, "Car2.txt", "a");
	if (fptr == NULL || fptr2 == NULL)
	{
		colourFunc(12); cout << "Fayli acmaq olmur!!!" << endl << endl;
		fclose(fptr2);
		remove("Car2.txt");
		exitPage(1);
	}
	else
	{
		while (fscanf(fptr, "%d %s %s %s %s %d %d %d %s\n", &car.id, car.mark, car.model, car.numberPlate, car.colour, &car.maxSpeed, &car.dailyRent, &car.year, car.carisrented) != -1)
		{
			if (id == car.id && strcmp(car.carisrented, "No") == 0)
			{
				value = 1;
			}
			else if (id == car.id && strcmp(car.carisrented, "Yes") == 0)
			{
				value = 2;
				fprintf_s(fptr2, "%d %s %s %s %s %d %d %d %s\n", car.id, car.mark, car.model, car.numberPlate, car.colour, car.maxSpeed, car.dailyRent, car.year, car.carisrented);
			}
			else fprintf_s(fptr2, "%d %s %s %s %s %d %d %d %s\n", car.id, car.mark, car.model, car.numberPlate, car.colour, car.maxSpeed, car.dailyRent, car.year, car.carisrented);
		}
		fclose(fptr);
		fclose(fptr2);
		remove("Car.txt");
		rename("Car2.txt", "Car.txt");
		if (value == 0)
		{
			colourFunc(12); cout << id << " Mashinin id- nomresi tapilmadi!!!" << endl << endl;
			remove("Car2.txt");
			exitPage(1);
		}

		else if (value == 2)
		{
			colourFunc(12); cout << "Bu mashini sile bilmezsiniz . Chunki bu mashin hazirda kirayededir " << endl << endl;
			exitPage(1);
		}

		else
		{
			colourFunc(10); cout << id << "Avtomobilin id-nomresin ugurla silinir!!!" << endl << endl;
			remove("Car2.txt");
			exitPage(1);
		}
	}
}

void userHomePage()
{
	system("cls");
	colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Hesabininza daxil olun" << endl;
	colourFunc(14); cout << "2"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Yeni hesab yaratmaq" << endl << endl;
	colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Back" << endl << endl;
	colourFunc(3); cout << "Etmek istediyniz emeliyyatin nomresini daxil edin: ";
	colourFunc(15); cin >> enter;
	if (enter[0] == '1' && enter[1] == '\0')
	{
		logUser();
	}
	else if (enter[0] == '0' && enter[1] == '\0')
	{
		firstPage();
	}
	else if (enter[0] == '2' && enter[1] == '\0')
	{
		createUser();
	}
	else
	{
		colourFunc(12); cout << endl << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin" << endl << endl;
		Sleep(4000);
		userHomePage();
	}
}

void createUser()
{
	system("cls");
	cin.ignore();
	colourFunc(14); cout << "Adinizi daxil edin: ";
	colourFunc(11); cin.getline(user.name, 20);
	colourFunc(14); cout << "Soyadinizi daxil edin: ";
	colourFunc(11); cin.getline(user.surname, 20);
	colourFunc(14); cout << "Shexsiyyet vesiqenizin nomresini daxil edin: ";
	colourFunc(11); cin.getline(user.cardSerialnum, 20);
	colourFunc(14); cout << "Mobil nomrenizi daxil edin: ";
	colourFunc(11); cin.getline(user.mobilNumber, 20);
	strcpy_s(user.login, user.name);
	strcpy_s(user.password, user.name);
	for (int i = strlen(user.login), j = 3; j < 6; i++, j++)
	{
		user.login[i] = user.mobilNumber[j];
		user.login[i + 1] = '\0';
		user.password[i] = user.mobilNumber[j];
		user.password[i + 1] = '\0';
	}
	colourFunc(14); cout << "Girish: "; colourFunc(11); cout << user.login << endl;
	colourFunc(14); cout << "Shifre: "; colourFunc(11); cout << user.password << endl << endl;
	FILE* fptr;
	fopen_s(&fptr, "UserAccount.txt", "a");
	if (fptr != NULL)
	{
		fprintf_s(fptr, "%s %s %s %s %s %s\n", user.name, user.surname, user.cardSerialnum, user.mobilNumber, user.login, user.password);
		fclose(fptr);
	}
	colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Back" << endl << endl;
	while (true)
	{
		colourFunc(3); cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: ";
		colourFunc(15); cin >> enter;
		if (enter[0] == '0' && enter[1] == '\0')
		{
			userHomePage();
		}
		else
		{
			colourFunc(12); cout << "Sechiminiz sehvdir. Yeniden cehd edin" << endl;
		}
	}
}

void logUser()
{
	readUserAccountList();
	system("cls");
	colourFunc(14); cout << "Girish: ";
	colourFunc(11); cin >> userLogIn.login;
	colourFunc(14); cout << "Shifre: ";
	colourFunc(11); cin >> userLogIn.password;
	bool check = false; // bu dəyişən daxil edilmiş istifadəçi məlumatlarının düzgün olub olmadığını yoxlayır
	short k = 0;     //yoxlama dəyişəninin doğru olacağı zaman i -yə bərabərdir
	for (int i = 0; i < 100; i++)
	{
		if (strcmp(userLogIn.login, allUsers[i].login) == 0 && strcmp(userLogIn.password, allUsers[i].password) == 0)
		{
			check = true;
			k = i;
		}
	}
	if (check == true)
	{
		strcpy(request.name, allUsers[k].name);
		strcpy(request.surname, allUsers[k].surname);
		strcpy(request.mobilNumber, allUsers[k].mobilNumber);
		strcpy(request.cardSerialnum, allUsers[k].cardSerialnum);
		usermenu();
	}
	else
	{
		colourFunc(12); cout << endl << "Girish ve ya shifre sehvdir!!!" << endl << endl;
		colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Back" << endl << endl;

		while (true)
		{
			colourFunc(3); cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: ";
			colourFunc(15); cin >> enter;
			if (enter[0] == '0' && enter[1] == '\0')
			{
				userHomePage();
			}
			else
			{
				colourFunc(12); cout << endl << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin" << endl << endl;
			}
		}

	}
}

void readUserAccountList()
{
	FILE* fptr;
	fopen_s(&fptr, "UserAccount.txt", "r");
	if (fptr != NULL)
	{
		h = 0;
		while (fscanf(fptr, "%s %s %s %s %s %s\n", &allUsers[h].name, &allUsers[h].surname, &allUsers[h].cardSerialnum, &allUsers[h].mobilNumber, &allUsers[h].login, &allUsers[h].password) != -1)
		{
			h++;
		}
		fclose(fptr);
	}
}

void homePage()
{
	system("cls");
	while (true)
	{
		colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Admin Menu" << endl;
		colourFunc(14); cout << "2"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "User Menu" << endl;
		colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Exit" << endl << endl;
		colourFunc(3); cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: ";
		colourFunc(15); cin >> enter;
		if (enter[0] == '1' && enter[1] == '\0')
		{
			adminControl();
		}
		else if (enter[0] == '0' && enter[1] == '\0')
		{
			exit(1);
		}
		else if (enter[0] == '2' && enter[1] == '\0')
		{
			userHomePage();
		}
		else
		{
			system("cls");
			colourFunc(12); cout << endl << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin" << endl << endl;
		}	
	}
}

void usermenu()
{
	system("cls");
	while (true)
	{
		colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Avtomobil siyahisni gosterin" << endl;
		colourFunc(14); cout << "2"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Avtomobil kirayelemek uchun sorgu gonderin" << endl;
		colourFunc(14); cout << "3"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Muqavile siyahinizi daxil edin" << endl;
		colourFunc(14); cout << "4"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Movcud kiraye muddetini artirin" << endl;
		colourFunc(14); cout << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Back" << endl << endl;

		colourFunc(3); cout << "Istifade etmek istediyiniz emeliyyatin nomresini daxil edin: ";
		colourFunc(15); cin >> enter;

		if (enter[0] == '1' && enter[1] == '\0')
		{
			showCarList(2);
		}
		else if (enter[0] == '2' && enter[1] == '\0')
		{
			readCarList();
			requestForCar();
		}
		else if (enter[0] == '3' && enter[1] == '\0')
		{
			customerContractList();
		}
		else if (enter[0] == '4' && enter[1] == '\0')
		{
			extendTime();
		}
		else if (enter[0] == '0' && enter[1] == '\0')
		{
			userHomePage();
		}
		else
		{
			system("cls");
			colourFunc(12); cout << endl << "Sechiminiz sehvdir yeniden cehd edin" << endl << endl;
		}
	}

}

void requestForCar()
{
	system("cls");
	colourFunc(14); cout << "Avtomobil id-ni daxil edin: ";
	colourFunc(11); cin >> request.id;
	colourFunc(14); cout << "Neche gun ishe goturmek istediyinizi daxil edin: ";
	colourFunc(11); cin >> request.day;
	int i = 0;
	int n = 0;
	while (allCarr[i].id != NULL)
	{
		if (allCarr[i].id == request.id)
		{
			readRequestlist();
			for (int t = 0; t < m; t++)
			{
				if (allRequest[t].id == request.id && strcmp(allRequest[t].cardSerialnum, request.cardSerialnum) == 0)
				{
					colourFunc(6); cout << "Hormetli mushteri, artiq bu avtomobil uchun sorgu gondermisiniz" << endl << endl;
					exitPage(2);
				}
			}
			if (strcmp(allCarr[i].carisrented, "Yes") == 0)
			{
				colourFunc(4); cout << "Hormetli mushteri. Bu avtomobil artiq bashqasi terefinden icareye goturulmushdur" << endl << endl;
				exitPage(2);
			}
			else
			{
				request.payment = allCarr[i].dailyRent * request.day;
				strcpy(request.status, "No");
				n = 1;
				break;
			}
		}
		i++;
	}
	if (n == 1)
	{
		colourFunc(14); cout << "Odeyeceyiniz mebleg :"; colourFunc(11); cout << request.payment << " AZN" << endl << endl;
		colourFunc(14); cout << "1"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Sorgu gondermek" << endl;
		colourFunc(14); cout << "2"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Emeliyyatdan imtina edin" << endl;
		while ((enter[0] == '1' && enter[1] == '\0') || (enter[0] == '2' && enter[1] == '\0'))
		{
			colourFunc(3); cout << "Etmek istediyiniz emeliyyatin nomresini daxil edin: ";
			colourFunc(15); cin >> enter;
			if (enter[0] == '1' && enter[1] == '\0')
			{
				FILE* fptr;
				fopen_s(&fptr, "Request.txt", "a");
				if (fptr != NULL)
				{
					fprintf_s(fptr, "%s %s %s %s %d %d %d %s\n", request.name, request.surname, request.mobilNumber, request.cardSerialnum, request.id, request.day, request.payment, request.status);
					fclose(fptr);
					colourFunc(10); cout << endl << "Isteyiniz Admin paneline gonderildi" << endl; colourFunc(7);
					exitPage(2);
				}
			}
			else if (enter[0] == '2' && enter[1] == '\0')
			{
				usermenu();
			}
			else
			{
				system("cls");
				colourFunc(12); cout << endl << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin" << endl << endl;
			}
		}

	}
	else
	{
		colourFunc(12); cout << endl << "Mashin tapilmadi!!!" << endl << endl;
		exitPage(2);
	}
}

void readCarList()
{
	FILE* fptr;
	fopen_s(&fptr, "Car.txt", "r");
	if (fptr == NULL)
	{

	}
	else
	{
		g = 0;
		while (fscanf(fptr, "%d %s %s %s %s %d %d %d %s\n", &allCarr[g].id, allCarr[g].mark, allCarr[g].model, allCarr[g].numberPlate, allCarr[g].colour, &allCarr[g].maxSpeed, &allCarr[g].dailyRent, &allCarr[g].year, allCarr[g].carisrented) != EOF)
		{
			g++;
		}
		fclose(fptr);
	}

}

void readRequestlist()
{
	FILE* fptr5;
	fopen_s(&fptr5, "Request.txt", "r");
	m = 0;
	if (fptr5 != NULL)
	{
		while (fscanf(fptr5, "%s %s %s %s %d %d %d %s\n", allRequest[m].name, allRequest[m].surname, allRequest[m].mobilNumber, allRequest[m].cardSerialnum, &allRequest[m].id, &allRequest[m].day, &allRequest[m].payment, allRequest[m].status) != EOF)
		{
			m++;
		}
		fclose(fptr5);
	}
}

void requestList()
{
	system("cls");
	FILE* fptr5;
	fopen_s(&fptr5, "Request.txt", "r");
	if (fptr5 == NULL)
	{
		colourFunc(12); cout << "\t\tIstek siyahisi boshdur!!!" << endl << endl;
		exitPage(1);
	}
	else
	{
		fclose(fptr5);
		fopen_s(&fptr5, "Request.txt", "r");
		if (fptr5 != NULL)
		{
			int i = 0;
			while (fscanf(fptr5, "%s %s %s %s %d %d %d %s\n", allRequest[i].name, allRequest[i].surname, allRequest[i].mobilNumber,
				allRequest[i].cardSerialnum, &allRequest[i].id, &allRequest[i].day, &allRequest[i].payment, allRequest[i].status) != EOF)
			{
				i++;
			}
			fclose(fptr5);
			for (int k = 0; k < i; k++)
			{
				colourFunc(15); cout << "------------------------------------" << endl;
				colourFunc(14); cout << "Ad: ";                     colourFunc(11);    cout << allRequest[k].name << endl;
				colourFunc(14); cout << "Soyad: ";                  colourFunc(11);    cout << allRequest[k].surname << endl;
				colourFunc(14); cout << "Mobil  nomre: ";            colourFunc(11);    cout << allRequest[k].mobilNumber << endl;
				colourFunc(14); cout << "Shexsiyyet vesiqesinin nomresi: ";     colourFunc(11);    cout << allRequest[k].cardSerialnum << endl;
				colourFunc(14); cout << "Avtomobil id-i: ";                   colourFunc(11);    cout << allRequest[k].id << endl;
				colourFunc(14); cout << "Icare gunlerinin sayi: "; colourFunc(11);    cout << allRequest[k].day << endl;
				colourFunc(14); cout << "Umumi odenish: ";            colourFunc(11);    cout << allRequest[k].payment << endl;
				colourFunc(14); cout << "Muqavile statusu: ";          colourFunc(11);    cout << allRequest[k].status << endl;
				colourFunc(15); cout << "------------------------------------" << endl << endl;
			}
		}
		exitPage(1);
	}
}

void approveContract()
{
	system("cls");
	colourFunc(14); cout << "Avtomobil id-ni daxil edin: ";
	colourFunc(11); cin >> acceptRequest.carId;
	colourFunc(14); cout << "Mushterinin shexsiyyet vesiqesinin nomresini daxil edin: ";
	colourFunc(11); cin >> acceptRequest.cardSerialnum;
	readRequestlist();
	readCarList();
	int a = 0;

	for (int i = 0; i < m; i++)
	{
		if (acceptRequest.carId == allRequest[i].id && strcmp(acceptRequest.cardSerialnum, allRequest[i].cardSerialnum) == 0)
		{
			a = 1;
			strcpy(contract.name, allRequest[i].name);
			strcpy(contract.surname, allRequest[i].surname);
			strcpy(contract.cardSerialnum, allRequest[i].cardSerialnum);
			strcpy(contract.mobilNumber, allRequest[i].mobilNumber);
			contract.carId = allRequest[i].id;
			contract.payment = allRequest[i].payment;
			contract.day = allRequest[i].day;
			dateTime(contract.starttime, contract.endtime, contract.day);
			strcpy(allRequest[i].status, "Yes");
			int j = 0;
			while (allCarr[j].id != NULL)
			{
				if (acceptRequest.carId == allCarr[j].id)
				{
					strcpy(allCarr[j].carisrented, "Yes");
				}
				j++;
			}
			break;
		}
	}
	if (a == 1)
	{
		FILE* fptr;
		FILE* fptr2;
		FILE* fptr3;
		fopen_s(&fptr, "Car2.txt", "a");
		fopen_s(&fptr2, "Contractlist.txt", "a");
		fopen_s(&fptr3, "Request2.txt", "a");
		if (fptr == NULL && fptr2 == NULL)
		{
			colourFunc(12); cout << "Fayli acmaq olmur!!!";
			fclose(fptr);
			fclose(fptr2);
			fclose(fptr3);
			remove("Request2.txt");
			exitPage(1);
		}
		else
		{
			for (int i = 0; i < m; i++)
			{
				if (acceptRequest.carId == allRequest[i].id && strcmp(acceptRequest.cardSerialnum, allRequest[i].cardSerialnum) == 0)
				{
					continue;
				}
				else fprintf_s(fptr3, "%s %s %s %s %d %d %d %s\n", allRequest[i].name, allRequest[i].surname, allRequest[i].mobilNumber, allRequest[i].cardSerialnum, allRequest[i].id, allRequest[i].day, allRequest[i].payment, allRequest[i].status);
			}
			fclose(fptr3);
			remove("Request.txt");
			rename("Request2.txt", "Request.txt");
			int p = 0;
			while (allCarr[p].id != NULL)
			{
				fprintf_s(fptr, "%d %s %s %s %s %d %d %d %s\n", allCarr[p].id, allCarr[p].mark, allCarr[p].model, allCarr[p].numberPlate, allCarr[p].colour, allCarr[p].maxSpeed, allCarr[p].dailyRent, allCarr[p].year, allCarr[p].carisrented);
				p++;
			}
			fclose(fptr);
			remove("Car.txt");
			rename("Car2.txt", "Car.txt");
			fprintf_s(fptr2, "%s %s %s %s %d %d %d %s %s\n", contract.name, contract.surname, contract.cardSerialnum, contract.mobilNumber, contract.carId, contract.day, contract.payment, contract.starttime, contract.endtime);
			fclose(fptr2);
			colourFunc(10); cout << endl << "Istek ugurla tesdiq edildi" << endl << endl;
			exitPage(1);
		}
	}
	else
	{
		colourFunc(12); cout << endl << "Bu parametrler uchun sorgu tapilmadi" << endl << endl;
		exitPage(1);
	}
}

void readContractList(int n)
{
	system("cls");
	FILE* fptr;
	fopen_s(&fptr, "Contractlist.txt", "r");
	if (fptr == NULL)
	{
		colourFunc(12); cout << endl << "Muqavile siyahisi boshdur" << endl << endl;
		exitPage(n);
	}
	else
	{
		f = 0;
		while (fscanf(fptr, "%s %s %s %s %d %d %d %s %s\n", allContract[f].name, allContract[f].surname, allContract[f].cardSerialnum, allContract[f].mobilNumber,
			&allContract[f].carId, &allContract[f].day, &allContract[f].payment, allContract[f].starttime, allContract[f].endtime) != EOF)
		{
			f++;
		}
		fclose(fptr);
	}
}

void showContractList()
{
	readContractList(1);
	for (int i = 0; i < f; i++)
	{
		cout << "------------------------------------" << endl;
		colourFunc(14); cout << "Ad: ";                     colourFunc(11);  cout << allContract[i].name << endl;
		colourFunc(14); cout << "Soyad: ";                  colourFunc(11);  cout << allContract[i].surname << endl;
		colourFunc(14); cout << "Shexsiyyet vesiqesinin nomresini daxil edin: ";     colourFunc(11);  cout << allContract[i].cardSerialnum << endl;
		colourFunc(14); cout << "Mobil nomre: ";            colourFunc(11);  cout << allContract[i].mobilNumber << endl;
		colourFunc(14); cout << "Avtomobil id-i: ";                   colourFunc(11);  cout << allContract[i].carId << endl;
		colourFunc(14); cout << "Icare gunlerinin sayi: "; colourFunc(11);  cout << allContract[i].day << endl;
		colourFunc(14); cout << "Umumi odenish: ";            colourFunc(11);  cout << allContract[i].payment << endl;
		colourFunc(14); cout << "Bashlama vaxti: ";               colourFunc(11);  cout << allContract[i].starttime << endl;
		colourFunc(14); cout << "Bitme vaxti: ";                 colourFunc(11);  cout << allContract[i].endtime << endl;
		cout << "------------------------------------" << endl << endl;
	}
	exitPage(1);
}

// Giriş səhifəsindən asılı olaraq idarəetmə səhifəsinə və ya istifadəçi səhifəsinə qayıdın
void exitPage(int n)
{
	colourFunc(14); cout << endl << "0"; colourFunc(12); cout << ")  "; colourFunc(7); cout << "Back" << endl;
	do
	{
		colourFunc(3); cout << endl << "Etmek istediyiniz emeliyyatin nomresini daxil edin: ";
		colourFunc(15); cin >> enter;
		if (enter[0] == '0' && enter[1] == '\0')
		{
			if (n == 1) adminPage();
			else usermenu();
		}
		else
		{
			colourFunc(12); cout << endl << "Sechiminiz sehvdir. Zehmet olmazsa bir daha cehd edin" << endl << endl;
		}
	} while (true);
}

// Müştərilər özlərinə aid olan bütün müqaviləni görə biləcəklər
void customerContractList()
{
	readContractList(2);
	bool checkList = false;
	for (int i = 0; i < f; i++)
	{
		if (strcmp(allContract[i].name, request.name) == 0 && strcmp(allContract[i].cardSerialnum, request.cardSerialnum) == 0)
		{
			cout << "------------------------------------" << endl;
			colourFunc(14); cout << "Avtomobil id-i: ";                   colourFunc(11);  cout << allContract[i].carId << endl;
			colourFunc(14); cout << "Icare gunlerinin sayi: "; colourFunc(11);  cout << allContract[i].day << endl;
			colourFunc(14); cout << "Umumi odenish: ";            colourFunc(11);  cout << allContract[i].payment << endl;
			colourFunc(14); cout << "Bashlama vaxti: ";               colourFunc(11);  cout << allContract[i].starttime << endl;
			colourFunc(14); cout << "Bitme vaxti: ";                 colourFunc(11);  cout << allContract[i].endtime << endl;
			cout << "------------------------------------" << endl << endl;
			checkList = true;
		}
	}
	if (checkList == false)
	{
		colourFunc(12); cout << endl << "Senin adina hech bir muqavile yoxdur" << endl << endl;
	}

	exitPage(2);
}

void removeRequest()
{
	colourFunc(14); cout << " Avtomobil id-ni daxil edin: ";
	colourFunc(11); cin >> deleteRequest.id;
	colourFunc(14); cout << " Mushterinin shexsiyyet vesiqesinin nomresini daxil edin: ";
	colourFunc(11); cin >> deleteRequest.cardSerialnum;
	bool checkId = false;
	readRequestlist();
	FILE* fptr;
	fopen_s(&fptr, "Request2.txt", "a");
	if (m != 0 && fptr != NULL)
	{
		for (int i = 0; i < m; i++)
		{
			if (deleteRequest.id == allRequest[i].id && strcmp(deleteRequest.cardSerialnum, allRequest[i].cardSerialnum) == 0)
			{
				checkId = true;
			}
			else
			{
				fprintf_s(fptr, "%s %s %s %s %d %d %d %s\n", allRequest[i].name, allRequest[i].surname, allRequest[i].mobilNumber,
					allRequest[i].cardSerialnum, allRequest[i].id, allRequest[i].day, allRequest[i].payment, allRequest[i].status);
			}
		}
		fclose(fptr);
		remove("Request.txt");
		rename("Request2.txt", "Request.txt");
	}
	if (checkId == true)
	{
		colourFunc(10); cout << endl << deleteRequest.id << " Sorgu sayi ugurla silindi" << endl << endl;
		exitPage(1);
	}
	if (m == 0 || checkId == false)
	{
		fclose(fptr);
		remove("Request2.txt");
		colourFunc(4); cout << endl << " Sorgu tapilmadi " << deleteRequest.id << " id " << endl;
		exitPage(1);
	}
}

void extendTime()
{
	readContractList(2);
	bool checkContract = false;
	for (int i = 0; i < f; i++)
	{
		if (strcmp(request.cardSerialnum, allContract[i].cardSerialnum) == 0)
		{
			checkContract = true;
		}
	}
	if (checkContract == false)
	{
		colourFunc(10); cout << endl << "Sizin adiniza muqavile yoxdur" << endl << endl;
		exitPage(2);
	}
	else
	{
		cout << "Avtomobil id-ni daxil edin: ";
		cin >> editContract.carId;
		cout << "Yeni icare gununun sayini daxil edin :";
		cin >> editContract.day;
		bool checkCarID = false;
		for (int i = 0; i < f; i++)
		{
			if (editContract.carId == allContract[i].carId)
			{
				if (editContract.day < allContract[0].day)
				{
					cout << "Yeni icare muddeti evvelkinden  daha uzun olmalidir";
					exitPage(2);
				}
				else
				{
					allContract[i].day = editContract.day;
					allContract[i].payment = editContract.payment / editContract.day * allContract[i].day;
					dateTime(editContract.starttime, editContract.endtime, editContract.day);
					strcpy(allContract[i].starttime, editContract.starttime);
					strcpy(allContract[i].endtime, editContract.endtime);
					checkCarID = true;
				}
			}
		}
		if (checkCarID == true)
		{
			remove("Contractlist.txt");
			FILE* fptr;
			fopen_s(&fptr, "Contractlist.txt", "a");
			if (fptr != NULL)
			{
				for (int i = 0; i < f; i++)
				{
					fprintf_s(fptr, "%s %s %s %s %d %d %d %s %s\n", allContract[i].name, allContract[i].surname, allContract[i].cardSerialnum, allContract[i].mobilNumber,
						allContract[i].carId, allContract[i].day, allContract[i].payment, allContract[i].starttime, allContract[i].endtime);
				}
				fclose(fptr);
			}
			colourFunc(10); cout << endl << "Muqavile isteyinize uygun olaraq deyishtirildi" << endl << endl;
			exitPage(2);
		}
		else
		{
			colourFunc(10); cout << endl << editContract.carId << "Id-nomresi tapilmadi" << endl << endl;
			exitPage(2);
		}

	}
}

void searchContract()
{
	readContractList(1);
	char customerName[20];
	colourFunc(11); cout << "Mushterinin adini daxil edin: ";
	colourFunc(14); cin >> customerName;
	bool checkName = false;
	for (int i = 0; i < f; i++)
	{
		if (strcmp(customerName, allContract[i].name) == 0)
		{
			cout << "------------------------------------" << endl;
			colourFunc(14); cout << "Ad: ";                     colourFunc(11);  cout << allContract[i].name << endl;
			colourFunc(14); cout << "Soyad: ";                  colourFunc(11);  cout << allContract[i].surname << endl;
			colourFunc(14); cout << "Shexsiyyet vesiqesinin nomresi: ";     colourFunc(11);  cout << allContract[i].cardSerialnum << endl;
			colourFunc(14); cout << "Mobil  nomre: ";            colourFunc(11);  cout << allContract[i].mobilNumber << endl;
			colourFunc(14); cout << "Avtomobil id-i: ";                   colourFunc(11);  cout << allContract[i].carId << endl;
			colourFunc(14); cout << "Icare gunlerinin sayi: "; colourFunc(11);  cout << allContract[i].day << endl;
			colourFunc(14); cout << "Umumi odenish: ";            colourFunc(11);  cout << allContract[i].payment << endl;
			colourFunc(14); cout << "Bashlama vaxti: ";               colourFunc(11);  cout << allContract[i].starttime << endl;
			colourFunc(14); cout << "Bitme vaxti: ";                 colourFunc(11);  cout << allContract[i].endtime << endl;
			cout << "------------------------------------" << endl << endl;
			checkName = true;
		}
	}
	if (checkName == false)
	{
		colourFunc(4); cout << endl << "Muqavile tapilmadi" << endl << endl;
		exitPage(1);
	}
	else exitPage(1);
}
void terminateContract()
{
	readContractList(1);
	readCarList();
	char name[20];
	char idCardNumber[10];
	int carIDNumber;
	cout << "Mushterinin adini daxil edin: ";
	cin >> name;
	cout << "Mushterinin shexsiyyet vesiqesinin nomresini daxil edin: ";
	cin >> idCardNumber;
	cout << "Avtomobil id- nomresini daxil edin: ";
	cin >> carIDNumber;
	bool checkContract = false;
	int num;
	for (int i = 0; i < f; i++)
	{
		if (strcmp(name, allContract[i].name) == 0 && strcmp(idCardNumber, allContract[i].cardSerialnum) == 0 && carIDNumber == allContract[i].carId)
		{
			num = i;
			remove("Car.txt");
			FILE* fptr2;
			fopen_s(&fptr2, "Car.txt", "a");
			for (int j = 0; j < g; j++)
			{
				if (allContract[i].carId == allCarr[j].id)
				{
					strcpy(allCarr[j].carisrented, "No");
				}
				fprintf_s(fptr2, "%d %s %s %s %s %d %d %d %s\n", allCarr[j].id, allCarr[j].mark, allCarr[j].model, allCarr[j].numberPlate,
					allCarr[j].colour, allCarr[j].maxSpeed, allCarr[j].dailyRent, allCarr[j].year, allCarr[j].carisrented);
			}
			fclose(fptr2);
			checkContract = true;
		}
	}

	if (checkContract == false)
	{
		colourFunc(4); cout << endl << "Muqavile siyahida tapilmadi" << endl << endl;
		exitPage(1);
	}
	else
	{
		remove("Contractlist.txt");
		FILE* fptr;
		fopen_s(&fptr, "Contractlist.txt", "a");
		if (fptr != NULL)
		{
			for (int i = 0; i < f; i++)
			{
				if (num != i)
				{
					fprintf_s(fptr, "%s %s %s %s %d %d %d %s %s\n", allContract[i].name, allContract[i].surname, allContract[i].cardSerialnum, allContract[i].mobilNumber,
						allContract[i].carId, allContract[i].day, allContract[i].payment, allContract[i].starttime, allContract[i].endtime);
				}
			}
			fclose(fptr);
		}
		colourFunc(10); cout << endl << "Elaqe siyahida ugurla silindi " << endl << endl;
		exitPage(1);
	}
}

void autoDeleteContract()
{
	readCarList();
	int num;
	bool fileCheck = false;
	FILE* fptr;
	fopen_s(&fptr, "Contractlist.txt", "r");
	if (fptr != NULL)
	{
		u = 0;
		while (fscanf(fptr, "%s %s %s %s %d %d %d %s %s\n", allContract[u].name, allContract[u].surname, allContract[u].cardSerialnum, allContract[u].mobilNumber,
			&allContract[u].carId, &allContract[u].day, &allContract[u].payment, allContract[u].starttime, allContract[u].endtime) != EOF)
		{
			u++;
		}
		fclose(fptr);
	}
	if (u > 0)
	{
		datefunc(today);
		for (int i = 0; i < u; i++)
		{
			if (strcmp(today, allContract[i].endtime) == 0)
			{
				num = i;
				fileCheck = true;
				remove("Car.txt");
				FILE* fptr2;
				fopen_s(&fptr2, "Car.txt", "a");
				for (int j = 0; j < g; j++)
				{
					if (allContract[i].carId == allCarr[j].id)
					{
						strcpy(allCarr[j].carisrented, "No");
					}
					fprintf_s(fptr2, "%d %s %s %s %s %d %d %d %s\n", allCarr[j].id, allCarr[j].mark, allCarr[j].model, allCarr[j].numberPlate,
						allCarr[j].colour, allCarr[j].maxSpeed, allCarr[j].dailyRent, allCarr[j].year, allCarr[j].carisrented);
				}
				fclose(fptr2);
			}
		}
		if (fileCheck == true)
		{
			remove("Contractlist.txt");
			FILE* fptr3;
			fopen_s(&fptr3, "Contractlist.txt", "a");
			if (fptr3 != NULL)
			{
				for (int i = 0; i < u; i++)
				{
					if (num != i)
					{
						fprintf_s(fptr3, "%s %s %s %s %d %d %d %s %s\n", allContract[i].name, allContract[i].surname, allContract[i].cardSerialnum, allContract[i].mobilNumber,
							allContract[i].carId, allContract[i].day, allContract[i].payment, allContract[i].starttime, allContract[i].endtime);
					}
				}
				fclose(fptr3);
			}
		}
	}

}
