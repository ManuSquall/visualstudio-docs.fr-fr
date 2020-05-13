---
title: 'Comment : Services de dépannage Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710751"
---
# <a name="how-to-troubleshoot-services"></a>Comment : Services de dépannage
Il ya plusieurs problèmes communs qui peuvent se produire lorsque vous essayez d’obtenir un service:

- Le service n’est pas enregistré avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Le service est demandé par type d’interface et non par type de service.

- Le VSPackage demandant le service n’a pas été situé.

- Le mauvais fournisseur de services est utilisé.

  Si le service demandé ne peut <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> être obtenu, l’appel aux retours nul. Vous devez toujours tester pour null après avoir demandé un service:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Pour dépanner un service

1. Examinez le registre du système pour voir si le service a été correctement enregistré. Pour plus d’informations, voir [Comment : Fournir un service](../extensibility/how-to-provide-a-service.md).

    Le fragment de fichier *.reg* suivant montre comment le service SVsTextManager peut être enregistré :

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Dans l’exemple ci-dessus, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]le numéro de version est la version de , tels que 12.0 ou 14.0, la clé 'F5E7E71D-1401-11d1-883B-0000F8779D2' est l’identifiant de service (SID) du service, SVsTextManager, et la valeur par défaut F5E7E720-1401-11d1-883B-0000F8779D2 est le paquet GUID du gestionnaire de texte VSPackage, qui fournit le service.

2. Utilisez le type de service et non le type d’interface lorsque vous appelez GetService. Lors de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]demande <xref:Microsoft.VisualStudio.Shell.Package> d’un service à partir , extrait le GUID du type. Un service ne sera pas trouvé si les conditions suivantes existent :

   1. Un type d’interface est transmis à GetService au lieu du type de service.

   2. Aucun GUID n’est explicitement attribué à l’interface. Par conséquent, le système crée un GUID par défaut pour un objet au besoin.

3. Assurez-vous que le VSPackage demandant le service a été situé. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sites un VSPackage après l’avoir construit et avant d’appeler <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.

    Si vous avez du code dans un constructeur VSPackage `Initialize` qui a besoin d’un service, déplacez-le vers la méthode.

4. Assurez-vous que vous utilisez le bon fournisseur de services.

    Tous les fournisseurs de services ne se ressemblent pas. Le fournisseur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de services qui passe à une fenêtre d’outil diffère de celui qu’il passe à un VSPackage. Le fournisseur de services <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>de fenêtre d’outil connaît, mais ne sait pas . <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Vous pouvez <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> appeler pour obtenir un fournisseur de services VSPackage à partir d’une fenêtre d’outils.

    Si une fenêtre d’outil héberge un contrôle utilisateur ou tout autre conteneur de contrôle, le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] conteneur sera situé par le modèle de composant Windows et n’aura accès à aucun service. Vous pouvez <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> appeler pour obtenir un fournisseur de services VSPackage à l’intérieur d’un conteneur de contrôle.

## <a name="see-also"></a>Voir aussi
- [Liste des services disponibles](../extensibility/internals/list-of-available-services.md)
- [Utiliser et fournir des services](../extensibility/using-and-providing-services.md)
- [Essentiels de service](../extensibility/internals/service-essentials.md)
