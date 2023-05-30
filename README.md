#include <iostream>
#include <string>
#include <vector>

using namespace std;

class Cab {
protected:
    string cab_type;
    double base_fare;
    double rate_per_km;

public:
    Cab(string type, double fare, double rate) : cab_type(type), base_fare(fare), rate_per_km(rate) {}
    virtual double calculate_fare(double distance) = 0;
    virtual void display_details() = 0;
};

class MicroCab : public Cab {
public:
    MicroCab() : Cab("Micro", 50, 10) {}
    double calculate_fare(double distance) {
        return base_fare + (distance * rate_per_km);
    }
    void display_details() {
        cout << "Cab Type: " << cab_type << ", Base Fare: " << base_fare << ", Rate per km: " << rate_per_km << endl;
    }
};

class MiniCab : public Cab {
public:
    MiniCab() : Cab("Mini", 75, 15) {}
    double calculate_fare(double distance) {
        return base_fare + (distance * rate_per_km);
    }
    void display_details() {
        cout << "Cab Type: " << cab_type << ", Base Fare: " << base_fare << ", Rate per km: " << rate_per_km << endl;
    }
};

class SedanCab : public Cab {
public:
    SedanCab() : Cab("Sedan", 100, 20) {}
    double calculate_fare(double distance) {
        return base_fare + (distance * rate_per_km);
    }
    void display_details() {
        cout << "Cab Type: " << cab_type << ", Base Fare: " << base_fare << ", Rate per km: " << rate_per_km << endl;
    }
};

int main() {
    vector<Cab*> cabs;
    cabs.push_back(new MicroCab());
    cabs.push_back(new MiniCab());
    cabs.push_back(new SedanCab());

    double distance;
    cout << "Enter the distance in km: ";
    cin >> distance;

    for (auto cab : cabs) {
        cab->display_details();
        cout << "Fare: " << cab->calculate_fare(distance) << endl;
        cout << endl;
    }

    return 0;
}
