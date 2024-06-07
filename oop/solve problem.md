```java
import java.time.LocalDate;
import java.time.Period;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

abstract  class MedicalDevices{
    public int serialNumber;
    public String Name;

    public LocalDate dateOfPurshace = LocalDate.now();

    public LocalDate getDateOfPurshace() {
        return dateOfPurshace;
    }
    abstract LocalDate getExpiredDate();

    public MedicalDevices(int serialNumber, String name) {
        this.serialNumber = serialNumber;
        Name = name;
    }
}
class PumpsDevices extends MedicalDevices{
    LocalDate expiredDate = LocalDate.now().plus(Period.ofYears(5));

    public    PumpsDevices(int serialNumber, String name){
        super(serialNumber,name);
    }

    public LocalDate getExpiredDate() {
        return expiredDate;
    }
}
class ImagingDevices extends MedicalDevices{
    LocalDate expiredDate = LocalDate.now().plus(Period.ofYears(10));

    public    ImagingDevices(int serialNumber, String name){
        super(serialNumber,name);
    }

    public LocalDate getExpiredDate() {
        return expiredDate;
    }
}

public class Inventory {
    public static List<MedicalDevices> storage = new ArrayList<>();
    public static void main(String[] args) {
        storage.add(new PumpsDevices(155,"Syringe1"));
        storage.add(new PumpsDevices(155,"Syringe2"));
        storage.add(new PumpsDevices(155,"Syringe"));
        storage.add(new PumpsDevices(155,"Syringe"));
        storage.add(new ImagingDevices(1566,"Ct Scan"));


        scraped(storage);


    }
    public static int scraped(List<MedicalDevices> medicalDevices){
        java.util.Iterator<MedicalDevices> iterator = medicalDevices.iterator();
        int count = 0;
        while(iterator.hasNext()){
            MedicalDevices medicalDevice = iterator.next();
            if (medicalDevice.getDateOfPurshace().isAfter(medicalDevice.getExpiredDate())){
                iterator.remove();
                count++;
            }
        }
        return count;
    }

}
```
