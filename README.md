# student-grade-manager
import java.util.ArrayList;
interface Evaluable {
    double calculerMoyenne();
}
class Exceptionnote extends Exception {
    public Exceptionnote(String message) {
        super(message);
    }
}
class Etudiant implements Evaluable {
    protected String nom;
    protected ArrayList<Double> notes = new ArrayList<>();
    public Etudiant(String nom) {
        this.nom = nom;
    }
    public void ajouternote(double note) {
        notes.add(note);
    }
    public void supprimernote(int index) {
        notes.remove(index);
    }
    public void modifiernote(int index, double nouvellenote) {
        notes.set(index, nouvellenote);
    }
    public double calculerMoyenne() {
        if (notes.isEmpty()) return 0;
        double somme = 0;
        for (double n : notes) {
            somme += n;
        }
        return somme / notes.size();
    }
    public void afficher() {
        System.out.println(nom + " sa moyenne est: " + calculerMoyenne());
    }
}
public class Main {
    public static void main(String[] args) {
        ArrayList<Etudiant> etudiants = new ArrayList<>();
        etudiants.add(new Etudiant("Ahmed"));
        etudiants.add(new Etudiant("Salma"));
        etudiants.get(0).ajouternote(15);
        etudiants.get(1).ajouternote(20);
        etudiants.get(0).ajouternote(12);
        etudiants.get(1).ajouternote(11);
        etudiants.get(0).supprimernote(0);
        etudiants.get(1).supprimernote(1);
        for (Etudiant e : etudiants) {
            if (e.nom.equals("Salma")) {
                System.out.println("l'étudiant existe");
                e.afficher();
            }
        }
    }
}
