---
title: "Comment&#160;: obtenir un service &#224; partir d’un thread d’arri&#232;re-plan (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multithreading, services"
ms.assetid: 97a56709-66d4-431a-ae63-392ee5898511
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Comment&#160;: obtenir un service &#224; partir d’un thread d’arri&#232;re-plan (C++)
Les services ne peuvent pas être obtenu à l'aide d' `IServiceProvider.QueryService` d'un thread d'arrière\-plan.  Si vous utilisez `QueryService` pour obtenir un service sur le thread principal, puis essayez d'utiliser le service sur un thread d'arrière\-plan, il échouera également.  
  
 Pour obtenir un service d'un thread d'arrière\-plan, utilisez `CoMarshalInterThreadInterfaceInStream` dans la méthode d' `IVsPackage.SetSite` pour marshaler le fournisseur de services dans un flux de données sur le thread principal.  Vous pouvez ensuite unmarshal le fournisseur de services sur un thread d'arrière\-plan et l'utiliser pour obtenir le service.  Vous pouvez unmarshal une seule fois, donc mettez en cache l'interface qui vous aide à prendre en arrière.  
  
> [!NOTE]
>  Le code managé marshale automatiquement des interfaces entre les threads, donc l'obtention d'un service d'un thread d'arrière\-plan ne requiert pas de code spécial.  
  
## Exemple  
 Le code suivant marshale un fournisseur de services dans le thread principal et fournit une méthode d' `QueryServiceFromBackgroundThread` à unmarshal le fournisseur de services pour obtenir un service d'un thread d'arrière\-plan.  
  
```  
class CMyPackage : public IVsPackage  
{  
private:  
    // Used to marshal IServiceProvider between threads  
    CComPtr< IStream > m_pSPStream;  
    // IServiceProvider proxy for the background thread  
    CComPtr< IServiceProvider > m_pBackgroundSP;  
  
public:  
    HRESULT SetSite( IServiceProvider* pSP )  
    {  
        // Marshal the service provider into a stream so that  
        // the background thread can retrieve it later  
        CoMarshalInterThreadInterfaceInStream(  
            IID_IServiceProvider, pSP, &m_pSPStream);  
  
        //... do the rest of your initialization  
    }  
  
    // Call this when your background thread needs to call QueryService  
    // The first time through, it unmarshals the interface stored   
    HRESULT QueryServiceFromBackgroundThread(  
        REFGUID rsid,        // [in] Service ID  
        REFIID riid,         // [in] Interface ID  
        // [out] Interface pointer of requested service (NULL on error)  
        void **ppvObj  
    {  
        if( !m_pBackgroundSP )  
        {  
            if( !m_pSPStream )  
            {  
                return E_UNEXPECTED;  
            }  
  
            HRESULT hr = CoGetInterfaceAndReleaseStream(   
                m_pSPStream, IID_IServiceProvider,   
                (void **)&m_pBackgroundSP );  
            if( FAILED(hr) )  
            {  
                return hr;  
            }  
  
            // The CoGetInterfaceAndReleaseStream has already   
            // destroyed the stream.  To avoid double-freeing,   
            // the smart wrapper needs to be detached.  
            m_pSPStream.Detach();  
        }  
  
        return m_pBackgroundSP->QueryService( rsid, riid, ppvObj );  
    }  
};  
```  
  
## Voir aussi  
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)