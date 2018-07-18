---
title: 'Comment : dépanner les Services | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9efe3c1c7032f1db41272a03cf689e015a79522
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128673"
---
# <a name="how-to-troubleshoot-services"></a>Comment : dépanner les Services
Il existe plusieurs problèmes courants qui peuvent se produire lorsque vous essayez d’obtenir un service :  
  
-   Le service n’est pas enregistré avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Le service est demandé par type d’interface et non par type de service.  
  
-   Le VSPackage demandant le service n’a pas été placé.  
  
-   Le fournisseur de services incorrect est utilisé.  
  
 Si le service demandé ne peut pas être obtenue à l’appel de <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> retourne la valeur null. Vous devez toujours tester null après la demande d’un service :  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Pour résoudre les problèmes d’un service  
  
1.  Examinez le Registre système pour voir si le service a été correctement inscrit. Pour plus d’informations, consultez [Comment : fournir un Service](../extensibility/how-to-provide-a-service.md).  
  
     Le fragment de fichier .reg suivant montre comment le service de SVsTextManager peut être inscrit :  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], telle que 12.0 ou 14.0, la clé {F5E7E71D-1401-11d1-883B-0000F87579D2} est l’identificateur de service (SID) du service, SVsTextManager et la {de valeur par défaut F5E7E720-1401-11D1-883B-0000F87579D2} est le GUID du Gestionnaire de texte VSPackage, qui fournit le service du package.  
  
2.  Lorsque vous appelez la méthode GetService, utilisez le type de service et pas le type d’interface. Lors de la demande d’un service à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrait le GUID du type. Un service sera introuvable si les conditions suivantes sont réunies :  
  
    1.  Un type d’interface est passé à GetService au lieu du type de service.  
  
    2.  Aucun GUID n’est explicitement affectée à l’interface. Par conséquent, le système crée un GUID par défaut pour un objet en fonction des besoins.  
  
3.  Assurez-vous que le VSPackage demandant le service a été installé. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sites d’un VSPackage après la construction et avant d’appeler <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Si vous disposez du code dans un constructeur de VSPackage qui a besoin d’un service, déplacez-le à la méthode Initialize.  
  
4.  N’oubliez pas que vous utilisez le fournisseur de service approprié.  
  
     Tous les fournisseurs de service sont identiques. Le fournisseur de services qui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] transmet à une fenêtre outil diffère de celui qu’il transmet à un VSPackage. Le fournisseur de services de fenêtre outil connaît <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, mais ne connaît ne pas <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour obtenir un fournisseur de service VSPackage dans une fenêtre outil.  
  
     Si une fenêtre outil héberge un contrôle utilisateur ou tout autre conteneur de contrôle, le conteneur sera doit se trouver par le modèle de composant Windows et qu’il n’aura pas accès à aucun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour obtenir un fournisseur de services VSPackage à partir d’un conteneur de contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des Services disponibles](../extensibility/internals/list-of-available-services.md)   
 [À l’aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)