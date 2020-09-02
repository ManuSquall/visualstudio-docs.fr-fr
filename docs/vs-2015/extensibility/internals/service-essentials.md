---
title: Notions fondamentales sur service | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696079"
---
# <a name="service-essentials"></a>Éléments fondamentaux du service
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un service est un contrat entre deux VSPackages. Un VSPackage fournit un ensemble spécifique d’interfaces à utiliser par un autre VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est lui-même une collection de VSPackages qui fournit des services à d’autres VSPackages.  
  
 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire dans le journal d’activité. Pour plus d’informations, consultez [procédure : utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit également des services intégrés qui ne sont pas inscrits. Les VSPackages peuvent remplacer des services intégrés ou d’autres services en fournissant une substitution de service. Une seule substitution de service est autorisée pour n’importe quel service.  
  
 Les services n’ont pas de détectabilité. Par conséquent, vous devez connaître l’identificateur de service (SID) d’un service que vous souhaitez utiliser, et vous devez connaître les interfaces qu’il fournit. La documentation de référence pour le service fournit ces informations.  
  
- Les VSPackages qui fournissent des services sont appelés fournisseurs de services.  
  
- Les services fournis à d’autres VSPackages sont appelés services globaux.  
  
- Les services qui sont disponibles uniquement pour le VSPackage qui les implémente, ou pour tout objet qu’il crée, sont appelés services locaux.  
  
- Les services qui remplacent les services intégrés ou les services fournis par d’autres packages sont appelés des substitutions de service.  
  
- Les services, ou substitutions de service, sont chargés à la demande, autrement dit, le fournisseur de services est chargé lorsque le service qu’il fournit est demandé par un autre VSPackage.  
  
- Pour prendre en charge le chargement à la demande, un fournisseur de services inscrit ses services globaux auprès de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pour plus d’informations, consultez la page [inscription de services](../../misc/registering-services.md).  
  
- Après avoir obtenu un service, utilisez [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (code non managé) ou une conversion (code managé) pour obtenir l’interface souhaitée, par exemple :  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Le code managé fait référence à un service par son type, alors que le code non managé fait référence à un service par son GUID.  
  
- Lorsque [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge un VSPackage, il passe un fournisseur de services au VSPackage pour accorder l’accès au VSPackage aux services globaux. C’est ce que l’on appelle le VSPackage.  
  
- Les VSPackages peuvent être des fournisseurs de services pour les objets qu’ils créent. Par exemple, un formulaire peut envoyer une demande de service de couleur à son Frame, qui peut passer la demande à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Les objets managés qui sont profondément imbriqués, ou qui ne sont pas sur site, peuvent appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour un accès direct aux services globaux. Pour plus d’informations, consultez [How to : Use GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des services disponibles](../../extensibility/internals/list-of-available-services.md)   
 [Utilisation et fourniture de services](../../extensibility/using-and-providing-services.md)   
 [Cast et conversions de types](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Transtypage](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
