---
title: "Comment : r&#233;soudre les probl&#232;mes des Services | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dépannage des services"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment : r&#233;soudre les probl&#232;mes des Services
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il existe plusieurs problèmes courants qui peuvent se produire lorsque vous essayez d'obtenir un service :  
  
-   Le service n'est pas enregistré avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Le service est demandé par type d'interface et non par type de service.  
  
-   Le VSPackage demandant le service n'a pas été placé.  
  
-   Le fournisseur de services incorrect est utilisé.  
  
 Si le service demandé n'aboutit pas, l'appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> renvoie la valeur null. Vous devez toujours tester null après avoir demandé un service :  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### Pour résoudre les problèmes d'un service  
  
1.  Examinez le Registre système pour voir si le service a été correctement inscrit. Pour plus d'informations, consultez [Inscription de services](../misc/registering-services.md).  
  
     Le fragment de fichier .reg suivant montre comment le service SVsTextManager peut être enregistré :  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     Dans l'exemple ci\-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], telles que 12.0 ou 14.0, la clé {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} est l'identificateur de service \(SID\) du service, SVsTextManager, et la valeur par défaut {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} est le GUID du Gestionnaire de texte VSPackage, qui fournit le service de package.  
  
2.  Lorsque vous appelez la méthode GetService, utilisez le type de service et pas le type d'interface. Lors de la demande d'un service à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrait le GUID du type. Un service sera introuvable si les conditions suivantes sont réunies :  
  
    1.  Un type interface est passé à la méthode GetService au lieu du type de service.  
  
    2.  Aucun GUID n'est explicitement affectée à l'interface. Par conséquent, le système crée un GUID par défaut pour un objet en fonction des besoins.  
  
3.  Assurez\-vous que le VSPackage demandant le service a été installé.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sites un VSPackage après la construction et avant d'appeler <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Si vous avez le code dans un constructeur VSPackage qui a besoin d'un service, déplacez\-le vers la méthode Initialize.  
  
4.  N'oubliez pas que vous utilisez le fournisseur de service correct.  
  
     Tous les fournisseurs de service sont similaires. Le fournisseur de services qui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] transmet à une fenêtre outil diffère de celui qu'il transmet à un VSPackage. Le fournisseur de services de fenêtre outil connaît <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, mais ne connaît ne pas <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour accéder à un fournisseur de service VSPackage dans une fenêtre outil.  
  
     Si une fenêtre outil héberge un contrôle utilisateur ou tout autre conteneur de contrôle, le conteneur doit se trouver par le modèle de composant de Windows et qu'il n'aura pas accès à tout [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour obtenir un fournisseur de services VSPackage à partir d'un conteneur de contrôle.  
  
## Voir aussi  
 [Liste des Services disponibles](../extensibility/internals/list-of-available-services.md)   
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Service Essentials](../extensibility/internals/service-essentials.md)