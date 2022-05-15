#include <bits/stdc++.h>
using namespace std;
typedef long long ll;

const int maxn=1e5+3;
const ll inf=1e18;
const double PI=acos((double)(-1));
const double eps=1e-9;

struct Node
{
	int x,pos;
};
inline void slv()
{
	int n,sz;cin>>n>>sz;
	vector<Node>v;
	set<int>s;
	int cnt=0;
	
	for (int i=1;i<=n;i++)
	{
		int num;cin>>num;
		if (v.size() < sz)
		{
			v.push_back({num,cnt++});
			s.insert(num);
		}
		else 
		{
			if (s.find(num) != s.end()) continue;
			else 
			{
				int now=maxn,pre=-1;
				for (int j=0;j<v.size();j++)
				{
					if (now > v[j].pos) now=v[j].pos,pre=j;
				}
				cout<<v[pre].x<<" "<<pre<<endl;
				s.erase(v[pre].x);
				v[pre].x=num,v[pre].pos=cnt++;
			}
		}	
	}
}
int main()
{
    std::ios::sync_with_stdio(false);
    std::cin.tie(nullptr);

    slv();
    return 0;
}
