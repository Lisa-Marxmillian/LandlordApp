<img width="649" height="375" alt="Screenshot 2025-08-08 225432" src="https://github.com/user-attachments/assets/b144fb07-2c77-491d-b991-d1872126cd12" />

**1. Extend the TenantViewModel**
Add a MutableLiveData counter to track the number of tenants and expose it as LiveData:

class TenantViewModel : ViewModel()
{
    private val _tenantInfo = MutableLiveData<String>("")
    private val _tenantCount = MutableLiveData<Int>(0)  

    val tenantInfo: LiveData<String> = _tenantInfo
    val tenantCount: LiveData<Int> = _tenantCount  

    fun addTenant(name: String, unit: String, rent: String) {
        val newEntry = "Name: $name\nUnit: $unit\nRent: $rent\n\n"
        _tenantInfo.value = (_tenantInfo.value ?: "") + newEntry
        _tenantCount.value = (_tenantCount.value ?: 0) + 1 
    }
}

**2. Update the XML Layout**
Add a TextView to display the counter using Data Binding:

<TextView
    android:id="@+id/tvTenantCount"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text='@{"Tenants added: " + viewModel.tenantCount}'
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintStart_toStartOf="parent" />

_tenantCount: Tracks the count internally (MutableLiveData).

tenantCount: Exposes the count to the UI as read-only LiveData.

addTenant(): Updates both the tenant info string and increments the counter.

XML Binding: The TextView dynamically updates when tenantCount changes, thanks to LiveData + Data Binding.    
