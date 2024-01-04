# SouceCode_TUBES_PBO_A
// Class Meteran Listrik
public class MeteranListrik {
    private String id;
    private boolean rusak;

    public MeteranListrik(String id) {
        this.id = id;
        this.rusak = false;
    }
    public String getId() {
        return id;
    }
    public boolean isRusak() {
        return rusak;
    }
    public void setRusak(boolean rusak) {
        this.rusak = rusak;
    }
}


// Class PenangananMeteranListrik
import java.lang.reflect.Array;
import java.util.ArrayList;

public class PenangananMeteranListrik {
    private ArrayList<MeteranListrik> daftarMeteran = new ArrayList<>();

    public void tambahMeteranListrik(String id) {
        MeteranListrik meteran = new MeteranListrik(id);
        daftarMeteran.add(meteran);
    }
    public void tandaiMeteranRusak(String id) {
        MeteranListrik meteran = cariMeteranById(id);
        if (meteran != null) {
            meteran.setRusak(true);
            System.out.println("Meteran listrik dengan ID " + id + " telah ditandai sebagai rusak.");
        } else {
            System.out.println("Meteran listrik dengan ID " + id + " tidak ditemukan.");
        }
    }

    public MeteranListrik cariMeteranById(String id) {
        for (MeteranListrik meteran : daftarMeteran) {
            if (meteran.getId().equals(id)) {
                return meteran;
            }
        }
        return null;
    }
    public void tampilkanDaftarMeteran() {
        System.out.println("Daftar Meteran Listrik:");
        for (MeteranListrik meteran : daftarMeteran) {
            System.out.println("ID: " + meteran.getId() + ", Rusak: " + meteran.isRusak());
        }
    }
}


// Class Hasil Meteran Listrik
public class HasilMeteranListrik {
    private String id;
    private double hasil;

    public HasilMeteranListrik(String id, double hasil) {
        this.id = id;
        this.hasil = hasil;
    }
    public String getId() {
        return id;
    }
    public double getHasil() {
        return hasil;
    }
    public void setHasil(double hasil) {
        this.hasil = hasil;
    }
}


// Class Sarah
public class Sarah {
    private String nama;

    public Sarah(String nama) {
        this.nama = nama;
    }
    public void tanganiMeteranListrik(MeteranListrik meteran) {
        System.out.println("Sarah melaporkan listrik mati hidup dengan ID " + meteran.getId());
    }
}


// Class Petugas PLN
public class PetugasPLN {
    private String nama;

    public PetugasPLN(String nama) {
        this.nama = nama;
    }
    public void tanganiMeteranListrik(MeteranListrik meteran) {
        System.out.println("Petugas PLN " + nama + " menydari meteran listrik dengan ID telah rusak " + meteran.getId());
    }
}


// Class Main
public class Main {
    public static void main(String[] args) {
        PenangananMeteranListrik penangananMeteran = new PenangananMeteranListrik();
        PetugasPLN petugasPLN = new PetugasPLN("Rojak");
        Sarah sarah = new Sarah("Sarah");

        penangananMeteran.tambahMeteranListrik("8601963890");
        penangananMeteran.tampilkanDaftarMeteran();
        penangananMeteran.tandaiMeteranRusak("8601963890");
        penangananMeteran.tampilkanDaftarMeteran();
        HasilMeteranListrik hasilMeteran = new HasilMeteranListrik("MTR001", 150.5);
        System.out.println("Hasil Meteran Listrik - ID: " + hasilMeteran.getId() + ", Hasil: " + hasilMeteran.getHasil());
        petugasPLN.tanganiMeteranListrik(penangananMeteran.cariMeteranById("8601963890"));
        sarah.tanganiMeteranListrik(penangananMeteran.cariMeteranById("8601963890"));
    }
}
