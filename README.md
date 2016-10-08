# c-programming
#include <cmath>
int main()
{
    std::random_device rd;
    std::mt19937 gen(rd());
 
    // values near the mean are the most likely
    // standard deviation affects the dispersion of generated values from the mean
    std::uniform_real_distribution<> d(0,1);
 
    std::map<int, double> hist;
    for(int n=0; n<1000; ++n) {
        ++hist[d(gen)*10.0];
    }
    double error =0;
    for(auto p : hist) {
        std::cout << std::fixed << std::setprecision(4) << std::setw(2)
                  << p.first/10.0 << ' ' << std::string(p.second/100, '*') << '\n';
                  std::cout<<"The hz value is "<<p.second/100<<'\n';
                  error += fabs(1.0-p.second/100);
    }
    std::cout<<"The error for this distritbution is "<<error<<'\n';

}
