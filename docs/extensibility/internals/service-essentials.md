---
title: "Service Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services, essentials"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Service Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un service est un contrat entre les deux packages VS. Un VSPackage fournit un ensemble spécifique d'interfaces pour un autre VSPackage à consommer.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est elle\-même une collection de packages VS qui fournit des services aux autres VSPackages.  
  
 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire dans le journal d'activité. Pour plus d'informations, consultez [Comment : utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit également des services intégrés qui ne sont pas enregistrés. Les VSPackages peut remplacer intégrés ou d'autres services en fournissant un service de remplacement. Remplacement d'un seul service est autorisée pour n'importe quel service.  
  
 Les services n'ont aucune fonctionnalité de découverte. Par conséquent, vous devez connaître l'identificateur de service \(SID\) d'un service que vous souhaitez utiliser, et vous devez connaître les interfaces qu'il fournit. La documentation de référence pour le service fournit ces informations.  
  
-   Les packages VS qui fournissent des services sont appelés fournisseurs de services.  
  
-   Les services fournis aux autres packages VS sont appelés services globaux.  
  
-   Les services qui sont disponibles uniquement pour le VSPackage qui implémente les, ou à n'importe quel objet qu'il crée, sont appelés services locaux.  
  
-   Les services qui remplacent les services intégrés ou des services fournis par d'autres packages, sont appelés des remplacements de service.  
  
-   Des services ou des remplacements de service, sont chargées sur demande, autrement dit, le fournisseur de services est chargé lorsque le service qu'il fournit est demandé par un autre package VS.  
  
-   Pour prendre en charge le chargement à la demande, un fournisseur de services enregistre ses services globaux avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations, consultez [Inscription de services](../../misc/registering-services.md).  
  
-   Après avoir obtenu un service, utilisez [QueryInterface](/visual-cpp/atl/queryinterface) \(code non managé\) ou cast \(code managé\) pour obtenir l'interface de votre choix, par exemple :  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Le code managé fait référence à un service par son type, tandis que le code non managé fait référence à un service par son GUID.  
  
-   Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge un VSPackage, il passe un fournisseur de services pour le VSPackage, afin de donner l'accès VSPackage aux services globaux. Cela est appelé « emplacement » le VSPackage.  
  
-   Les VSPackages peuvent être des fournisseurs de services pour les objets qu'ils créent. Par exemple, un formulaire peut envoyer une demande pour un service de couleur à son image, qui peut transmettre la requête [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Les objets managés qui sont profondément imbriquées ou pas du tout, doit se trouver peuvent appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour accéder directement aux services globaux. Pour plus d'informations, consultez [Procédure : utilisation d’un GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## Voir aussi  
 [Liste des Services disponibles](../../extensibility/internals/list-of-available-services.md)   
 [À l'aide et fournir des Services](../../extensibility/using-and-providing-services.md)   
 [Cast et conversions de types](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Effectuer un cast](/visual-cpp/cpp/casting)