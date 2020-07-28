---
title: 'Comment : dépanner les services | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bfbe4b11c22d6cfd147783f9fb662843cf57fe9
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234950"
---
# <a name="how-to-troubleshoot-services"></a>Comment : dépanner des services
Il existe plusieurs problèmes courants qui peuvent se produire lorsque vous essayez d’obtenir un service :

- Le service n’est pas inscrit auprès de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Le service est demandé par le type d’interface et non par le type de service.

- Le VSPackage qui demande le service n’a pas été mis en place.

- Le mauvais fournisseur de services est utilisé.

  Si le service demandé ne peut pas être obtenu, l’appel à <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> retourne la valeur null. Vous devez toujours tester la valeur null après avoir demandé un service :

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Pour dépanner un service

1. Examinez le registre système pour voir si le service a été correctement inscrit. Pour plus d’informations, consultez [Comment : fournir un service](../extensibility/how-to-provide-a-service.md).

    Le fragment de fichier *. reg* suivant montre comment le service SVsTextManager peut être inscrit :

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , par exemple 12,0 ou 14,0, la clé {F5E7E71D-1401-11D1-883B-0000F87579D2} est l’identificateur de service (SID) du service, SVsTextManager, et la valeur par défaut {F5E7E720-1401-11D1-883B-0000F87579D2} est le GUID du package de Text Manager VSPackage, qui fournit le service.

2. Utilisez le type de service et non le type d’interface lorsque vous appelez GetService. Lors de la demande d’un service à partir de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , <xref:Microsoft.VisualStudio.Shell.Package> extrait le GUID du type. Un service ne sera pas trouvé si les conditions suivantes sont réunies :

   1. Un type interface est passé à GetService au lieu du type de service.

   2. Aucun GUID n’est explicitement affecté à l’interface. Par conséquent, le système crée un GUID par défaut pour un objet en fonction des besoins.

3. Assurez-vous que le VSPackage qui demande le service a été mis en place. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]site un VSPackage après l’avoir construit et avant d’appeler <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Si vous avez du code dans un constructeur VSPackage qui a besoin d’un service, déplacez-le vers la `Initialize` méthode.

4. Assurez-vous que vous utilisez le fournisseur de services approprié.

    Tous les fournisseurs de services ne sont pas identiques. Le fournisseur de services qui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passe à une fenêtre outil est différent de celui qu’il transmet à un VSPackage. Le fournisseur de services de la fenêtre outil connaît <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> , mais ne connaît pas <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour obtenir un fournisseur de services VSPackage dans une fenêtre outil.

    Si une fenêtre outil héberge un contrôle utilisateur ou tout autre conteneur de contrôle, le conteneur est installé par le modèle de composant Windows et n’a accès à aucun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] service. Vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour obtenir un fournisseur de services VSPackage à partir d’un conteneur de contrôle.

## <a name="see-also"></a>Voir aussi
- [Liste des services disponibles](../extensibility/internals/list-of-available-services.md)
- [Utilisez et fournissez des services](../extensibility/using-and-providing-services.md)
- [Notions de service Essentials](../extensibility/internals/service-essentials.md)
- [Résolution des problèmes de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)