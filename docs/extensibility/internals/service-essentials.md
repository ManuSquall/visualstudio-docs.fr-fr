---
title: Service Essentials | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>Service Essentials
Un service est un contrat entre deux VSPackages. Un VSPackage fournit un ensemble spécifique d’interfaces pour un autre VSPackage à consommer. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]est une collection de VSPackages qui fournit des services aux autres packages VS à elle-même.  
  
 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire dans le journal d’activité. Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit également des services intégrés qui ne sont pas enregistrés. Les VSPackages peuvent remplacer intégrés ou d’autres services en fournissant un service de remplacement. Remplacement d’un seul service est autorisée pour n’importe quel service.  
  
 Les services n’ont aucune fonctionnalité de découverte. Par conséquent, vous devez connaître l’identificateur de service (SID) d’un service que vous souhaitez utiliser, et vous devez connaître les interfaces qu’il fournit. La documentation de référence pour le service fournit ces informations.  
  
-   Les VSPackages qui fournissent des services sont appelés fournisseurs de services.  
  
-   Les services qui sont fournis pour les autres packages VS sont appelés services globaux.  
  
-   Services qui sont disponibles uniquement pour le VSPackage qui implémente les, ou à n’importe quel objet, qu'il crée, sont appelés des services locaux.  
  
-   Les services qui remplacent les services intégrés ou des services fournis par d’autres packages, sont appelés des remplacements de service.  
  
-   Des services ou des remplacements de service, sont chargées à la demande, autrement dit, le fournisseur de services est chargé lorsque le service à que fournir est demandé par un autre VSPackage.  
  
-   Pour prendre en charge le chargement de la demande, un fournisseur de services inscrit ses services globaux avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [enregistrement des Services](../../misc/registering-services.md).  
  
-   Après avoir obtenu un service, utilisez [QueryInterface](/cpp/atl/queryinterface) (code non managé) ou effectuer un cast (code managé) pour obtenir l’interface de votre choix, par exemple :  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Le code managé fait référence à un service par son type, alors que le code non managé fait référence à un service par son GUID.  
  
-   Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge un VSPackage, il passe un fournisseur de services pour le VSPackage pour donner l’accès VSPackage aux services globaux. Cela est appelé « emplacement » le VSPackage.  
  
-   Les VSPackages peuvent être des fournisseurs de services pour les objets qu’ils créent. Par exemple, un formulaire peut envoyer une demande pour un service de couleur à son cadre, ce qui peut transmettre la requête [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Les objets managés qui sont profondément imbriquées ou pas dans le site, peuvent appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>pour accéder directement aux services globaux.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Pour plus d’informations, consultez [Comment : utiliser GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des Services disponibles](../../extensibility/internals/list-of-available-services.md)   
 [À l’aide et fournir des Services](../../extensibility/using-and-providing-services.md)   
 [Cast et conversions de types](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Cast](/cpp/cpp/casting)
