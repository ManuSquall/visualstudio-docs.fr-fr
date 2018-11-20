---
title: Service Essentials | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90cec13c403194c70b9d44cff349b53495a0e160
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776458"
---
# <a name="service-essentials"></a>Éléments fondamentaux du service
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un service est un contrat entre deux VSPackages. Un VSPackage fournit un ensemble spécifique d’interfaces pour un autre package Visual Studio consommer. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est lui-même une collection de VSPackages qui fournit des services aux autres VSPackages.  
  
 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire dans le journal d’activité. Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit également des services intégrés qui ne sont pas enregistrées. VSPackages peut remplacer intégrés ou d’autres services en fournissant un service de remplacement. Remplacement d’un seul service est autorisée pour n’importe quel service.  
  
 Les services n’ont aucune fonctionnalité de découverte. Par conséquent, vous devez connaître l’identificateur de service (SID) d’un service que vous souhaitez utiliser, et vous devez connaître les interfaces qu’il fournit. La documentation de référence pour le service fournit ces informations.  
  
-   Les VSPackages qui fournissent des services sont appelés fournisseurs de services.  
  
-   Les services fournis aux autres packages VS sont appelés des services globaux.  
  
-   Les services qui sont disponibles uniquement pour le VSPackage qui implémente les, ou pour tout objet qu’elle crée, sont appelés des services locaux.  
  
-   Les services qui remplacent les services intégrés ou des services fournis par d’autres packages, sont appelés des remplacements de service.  
  
-   Services ou les remplacements de service, sont chargées à la demande, autrement dit, le fournisseur de services est chargé lorsque le service qu’il fournit est demandé par un autre package Visual Studio.  
  
-   Pour prendre en charge le chargement à la demande, un fournisseur de services enregistre ses services globaux auprès [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [enregistrement des Services](../../misc/registering-services.md).  
  
-   Après avoir obtenu un service, utilisez [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (code non managé) ou d’un transtypage (code managé) pour obtenir l’interface souhaitée, par exemple :  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Le code managé fait référence à un service par son type, tandis que le code non managé fait référence à un service par son GUID.  
  
-   Lorsque [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge un VSPackage, il transmet un fournisseur de services au VSPackage pour accorder l’accès de package Visual Studio pour les services globaux. Cela est appelé « positionnement » le VSPackage.  
  
-   Les VSPackages peuvent être des fournisseurs de services pour les objets qu’ils créent. Par exemple, un formulaire peut envoyer une demande pour un service de couleur à son image, qui peut transmettre la requête [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Objets managés qui sont profondément imbriquées ou pas du tout, doit se trouver peuvent appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour accéder directement aux services globaux. Pour plus d’informations, consultez [Comment : utiliser GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des Services disponibles](../../extensibility/internals/list-of-available-services.md)   
 [À l’aide et fourniture de Services](../../extensibility/using-and-providing-services.md)   
 [Cast et conversions de types](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Cast](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

