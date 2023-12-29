# Exam_Z3_Matraieva
import java.util.Arrays;
import java.util.Comparator;

class Phone {
    private int id;
    private String lastName;
    private String firstName;
    private String patronymic;
    private String address;
    private String creditCardNumber;
    private double debit;
    private double credit;
    private int cityCallsTime;
    private int intercityCallsTime;

    public Phone(int id, String lastName, String firstName, String patronymic,
                 String address, String creditCardNumber, double debit, double credit,
                 int cityCallsTime, int intercityCallsTime) {
        this.id = id;
        this.lastName = lastName;
        this.firstName = firstName;
        this.patronymic = patronymic;
        this.address = address;
        this.creditCardNumber = creditCardNumber;
        this.debit = debit;
        this.credit = credit;
        this.cityCallsTime = cityCallsTime;
        this.intercityCallsTime = intercityCallsTime;
    }
    public String getLastName() {
        return lastName;
    }
    public String getFirstName() {
        return firstName;
    }
    public String getPatronymic() {
        return patronymic;
    }
    public int getCityCallsTime() {
        return cityCallsTime;
    }
    public int getIntercityCallsTime() {
        return intercityCallsTime;
    }
    public static Phone[] createPhoneArray() {
        Phone[] phones = {
                new Phone(1, "Музика", "Іван", "Іванович", "Київ", "1111222233334444", 100.0, 50.0, 30, 10),
                new Phone(2, "Ференс", "Владислав", "Валерійович", "Львів", "5555666677778888", 150.0, 20.0, 20, 15),
                new Phone(3, "Сукманюк", "Валерія", "Сергіївна", "Хмельницький", "4444333377778888", 200.0, 15.0, 10, 20),
        };
        return phones;
    }

    public static void printCityCallsExceedLimit(Phone[] phones, int limit) {
        System.out.println("Абоненти з часом міських розмов, що перевищує ліміт:");
        for (Phone phone : phones) {
            if (phone.getCityCallsTime() > limit) {
                System.out.println(phone.toString());
            }
        }
        System.out.println();
    }

    public static void printIntercityCallsUsers(Phone[] phones) {
        System.out.println("Абоненти, які користувалися міжміським зв'язком:");
        for (Phone phone : phones) {
            if (phone.getIntercityCallsTime() > 0) {
                System.out.println(phone.toString());
            }
        }
        System.out.println();
    }

    public static void printAlphabeticalOrder(Phone[] phones) {
        System.out.println("Абоненти в алфавітному порядку:");
        Arrays.sort(phones, Comparator.comparing(Phone::getLastName)
                .thenComparing(Phone::getFirstName)
                .thenComparing(Phone::getPatronymic));
        for (Phone phone : phones) {
            System.out.println(phone.toString());
        }
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Ім'я: " + lastName + " " + firstName + " " + patronymic +
                ", Адреса: " + address + ", Час міських розмов: " + cityCallsTime +
                ", Час міжміських розмов: " + intercityCallsTime;
    }
}

public class Main {
    public static void main(String[] args) {
        Phone[] phones = Phone.createPhoneArray();

        // a) Виведення інформації про абонентів, у яких час міських розмов перевищує заданий ліміт
        Phone.printCityCallsExceedLimit(phones, 25);

        // b) Виведення інформації про абонентів, які користувалися міжміським зв'язком
        Phone.printIntercityCallsUsers(phones);

        // c) Виведення інформації про абонентів в алфавітному порядку
        Phone.printAlphabeticalOrder(phones);
    }
}
