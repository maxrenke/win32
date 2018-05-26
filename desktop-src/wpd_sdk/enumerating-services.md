---
Description: Enumerating Services
ms.assetid: 6ee6eecb-3812-45c6-8b27-7dfd6fa82758
title: Enumerating Services
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
ms.prod: windows
ms.technology: desktop
---

# Enumerating Services

The WpdServicesApiSample application includes code that demonstrates how an application can enumerate all of the Contacts services found on any of the devices currently connected to a computer.

When the user chooses option "0" at the command line, the application invokes the **EnumerateContactsServices** method that is found in the ServiceEnumeration.cpp module. This method displays a list of all connected devices that support the Contacts service.

For example, if the WpdServiceSampleDriver is the only installed device, the application returns three fields of data: a Friendly Name ("Sample Device"), a Manufacturer ("Windows Portable Devices Group"), and, a Description ("Contacts Service Device 2000").

The **EnumerateContactsServices** method accomplishes the following tasks:

-   Creates an [**IPortableDeviceManager**](/windows/win32/PortableDeviceApi/nn-portabledeviceapi-iportabledevicemanager?branch=master) interface to handle enumeration of installed devices.
-   Creates an [**IPortableDeviceServiceManager**](/windows/win32/PortableDeviceAPI/nn-portabledeviceapi-iportabledeviceservicemanager?branch=master) interface to handle enumeration of the services on each device.
-   Iterates through the installed devices, searching for the Contacts service, and displays the device information for any device that supports this service.

The following code illustrates the **EnumerateContactsServices** method.


```C++
// Enumerates all Contacts Services, displaying the associated device of each service.
void EumerateContactsServices(CAtlArray<PWSTR>&amp; ContactsServicePnpIDs)
{
    HRESULT                                 hr              = S_OK;
    DWORD                                   cPnpDeviceIDs   = 0;
    PWSTR*                                  pPnpDeviceIDs   = NULL;
    CComPtr<IPortableDeviceManager>         pPortableDeviceManager;
    CComPtr<IPortableDeviceServiceManager>  pServiceManager;

    // CoCreate the IPortableDeviceManager interface to enumerate
    // portable devices and to get information about them.
    hr = CoCreateInstance(CLSID_PortableDeviceManager,
                          NULL,
                          CLSCTX_INPROC_SERVER,
                          IID_PPV_ARGS(&amp;pPortableDeviceManager));

    if (FAILED(hr))
    {
        printf("! Failed to CoCreateInstance CLSID_PortableDeviceManager, hr = 0x%lx\n",hr);
    }        

    // Retrieve the IPortableDeviceServiceManager interface to enumerate device services.
    if (SUCCEEDED(hr))
    {
        hr = pPortableDeviceManager->QueryInterface(IID_PPV_ARGS(&amp;pServiceManager));
        if (FAILED(hr))
        {
            printf("! Failed to QueryInterface IID_IPortableDeviceServiceManager, hr = 0x%lx\n",hr);
        }
    }

    if (SUCCEEDED(hr))
    {
        // First, pass NULL as the PWSTR array pointer to get the total number
        // of devices found on the system.
        hr = pPortableDeviceManager->GetDevices(NULL, &amp;cPnpDeviceIDs);

        if (FAILED(hr))
        {
            printf("! Failed to get number of devices on the system, hr = 0x%lx\n",hr);
        }

        if (SUCCEEDED(hr) &amp;&amp; (cPnpDeviceIDs > 0))
        {
            // Second, allocate an array to hold the PnPDeviceID strings returned from
            // the IPortableDeviceManager::GetDevices method
            pPnpDeviceIDs = new (std::nothrow) PWSTR[cPnpDeviceIDs];

            if (pPnpDeviceIDs != NULL)
            {
                DWORD dwIndex = 0;

                hr = pPortableDeviceManager->GetDevices(pPnpDeviceIDs, &amp;cPnpDeviceIDs);
                if (SUCCEEDED(hr))
                {   
                    // For each device found, find the contacts service
                    for (dwIndex = 0; dwIndex < cPnpDeviceIDs; dwIndex++)
                    {
                        DWORD   cPnpServiceIDs = 0;
                        PWSTR   pPnpServiceID  = NULL;

                        // First, pass NULL as the PWSTR array pointer to get the total number
                        // of contacts services (SERVICE_Contacts) found on the device.
                        // To find the total number of all services on the device, use GUID_DEVINTERFACE_WPD_SERVICE.
                        hr = pServiceManager->GetDeviceServices(pPnpDeviceIDs[dwIndex], SERVICE_Contacts, NULL, &amp;cPnpServiceIDs);
                        
                        if (SUCCEEDED(hr) &amp;&amp; (cPnpServiceIDs > 0))
                        {                               
                            // For simplicity, we are only using the first contacts service on each device
                            cPnpServiceIDs = 1;
                            hr = pServiceManager->GetDeviceServices(pPnpDeviceIDs[dwIndex], SERVICE_Contacts, &amp;pPnpServiceID, &amp;cPnpServiceIDs);

                            if (SUCCEEDED(hr))
                            {
                                // We've found the service, display it and save its PnP Identifier
                                ContactsServicePnpIDs.Add(pPnpServiceID);

                                printf("[%d] ", static_cast<DWORD>(ContactsServicePnpIDs.GetCount()-1));

                                // Display information about the device that contains this service.
                                DisplayDeviceInformation(pServiceManager, pPnpServiceID);

                                // ContactsServicePnpIDs now owns the memory for this string
                                pPnpServiceID = NULL;
                            }
                            else
                            {
                                printf("! Failed to get the first contacts service from '%ws, hr = 0x%lx\n",pPnpDeviceIDs[dwIndex],hr);
                            }
                        }
                    }
                }

                // Free all returned PnPDeviceID strings
                FreePortableDevicePnPIDs(pPnpDeviceIDs, cPnpDeviceIDs);

                // Delete the array of PWSTR pointers
                delete [] pPnpDeviceIDs;
                pPnpDeviceIDs = NULL;

            }
            else
            {
                printf("! Failed to allocate memory for PWSTR array\n");
            }            
        }
    }
    
    printf("\n%d Contacts Device Service(s) found on the system\n\n", static_cast<DWORD>(ContactsServicePnpIDs.GetCount()));
}
```



## Related topics

<dl> <dt>

[**IPortableDeviceManager Interface**](/windows/win32/PortableDeviceApi/nn-portabledeviceapi-iportabledevicemanager?branch=master)
</dt> <dt>

[**IPortableDeviceServiceManager Interface**](/windows/win32/PortableDeviceAPI/nn-portabledeviceapi-iportabledeviceservicemanager?branch=master)
</dt> <dt>

[WpdServicesApiSample](wpdapisample-sample-service-application.md)
</dt> </dl>

 

 


