<img width="649" height="375" alt="Screenshot 2025-08-08 225432" src="https://github.com/user-attachments/assets/b144fb07-2c77-491d-b991-d1872126cd12" />

**1. Extend the TenantViewModel**
Add a MutableLiveData counter to track the number of tenants and expose it as LiveData:

<img width="690" height="399" alt="image" src="https://github.com/user-attachments/assets/a935d56b-3141-41d8-b873-5d5b18800c46" />


**2. Update the XML Layout**
Add a TextView to display the counter using Data Binding:

<img width="679" height="202" alt="image" src="https://github.com/user-attachments/assets/c2e2c757-816d-46d4-a45e-f4137148536f" />


_tenantCount: Tracks the count internally (MutableLiveData).

tenantCount: Exposes the count to the UI as read-only LiveData.

addTenant(): Updates both the tenant info string and increments the counter.

XML Binding: The TextView dynamically updates when tenantCount changes, thanks to LiveData + Data Binding.    
