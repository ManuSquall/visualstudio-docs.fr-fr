---
title: Essentiels du service Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8817ca48ff0a3f44a973986a173e647ce89c662c
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303238"
---
# <a name="service-essentials"></a>Éléments fondamentaux du service
Un service est un contrat entre deux VSPackages. Un VSPackage fournit un ensemble spécifique d’interfaces pour un autre VSPackage à consommer. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]est lui-même une collection de VSPackages qui fournit des services à d’autres VSPackages.

 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire au journal d’activité. Pour plus d’informations, voir [Comment : Utilisez le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit également des services intégrés qui ne sont pas enregistrés. VSPackages peut remplacer les services intégrés ou autres en fournissant un remplacement de service. Un seul remplacement de service est autorisé pour n’importe quel service.

 Les services n’ont pas de découverte. Par conséquent, vous devez connaître l’identifiant de service (SID) d’un service que vous voulez consommer, et vous devez savoir quelles interfaces il fournit. La documentation de référence pour le service fournit cette information.

- LES VSPackages qui fournissent des services sont appelés fournisseurs de services.

- Les services fournis à d’autres VSPackages sont appelés services mondiaux.

- Les services qui ne sont disponibles que pour le VSPackage qui les implémente, ou à tout objet qu’il crée, sont appelés services locaux.

- Les services qui remplacent les services intégrés ou les services fournis par d’autres forfaits sont appelés remplacements de service.

- Les services, ou remplacements de service, sont chargés à la demande, c’est-à-dire que le fournisseur de services est chargé lorsque le service qu’il fournit est demandé par un autre VSPackage.

- Pour soutenir le chargement à la demande, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]un fournisseur de services enregistre ses services mondiaux avec . Pour plus d’informations, voir [Comment : Fournir un service](../../extensibility/how-to-provide-a-service.md).

- Après avoir obtenu un service, utilisez [QueryInterface](/cpp/atl/queryinterface) (code non géré) ou le casting (code géré) pour obtenir l’interface désirée, par exemple :

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Le code géré désigne un service par son type, tandis que le code non géré se réfère à un service par son GUID.

- Lorsqu’il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge un VSPackage, il transmet un fournisseur de services à l’emballage VS pour donner au VSPackage l’accès aux services mondiaux. C’est ce qu’on appelle le « siting » le VSPackage.

- VSPackages peut être fournisseur de services pour les objets qu’ils créent. Par exemple, un formulaire peut envoyer une demande de service de couleur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]à son cadre, ce qui pourrait passer la demande à .

- Les objets gérés qui sont profondément imbriqués, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ou non du tout classés, peuvent appeler à un accès direct aux services mondiaux.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Utiliser GetGlobalService

Parfois, vous pouvez avoir besoin d’obtenir un service à partir d’une fenêtre d’outils ou un conteneur de contrôle qui n’a pas été situé, ou bien a été situé avec un fournisseur de services qui ne sait pas sur le service que vous voulez. Par exemple, vous pouvez écrire au journal d’activité à partir d’un contrôle. Pour plus d’informations sur ces scénarios et d’autres, voir [Comment : Services de dépannage](../../extensibility/how-to-troubleshoot-services.md).

Vous pouvez obtenir la plupart des <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> services Visual Studio en appelant la méthode statique.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>s’appuie sur un fournisseur de services mis en cache qui est paralésé la première fois que tout VSPackage dérivé de Package est situé. Vous devez garantir que cette condition est remplie, ou bien être prêt pour un service nul.

Heureusement, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> fonctionne correctement la plupart du temps.

- Si un VSPackage fournit un service connu uniquement d’un autre VSPackage, le VSPackage demandant le service est situé avant que le VSPackage fournissant le service est chargé.

- Si une fenêtre d’outil est créée par un VSPackage, le VSPackage est situé avant la création de la fenêtre d’outils.

- Si un conteneur de contrôle est hébergé par une fenêtre d’outils créée par un VSPackage, le VSPackage est situé avant la création du conteneur de commande.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Pour obtenir un service à partir d’une fenêtre d’outil ou d’un conteneur de contrôle

- Insérez ce code dans le constructeur, la fenêtre d’outils ou le conteneur de contrôle :

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Ce code obtient un service SVsActivityLog et le jette sur une interface IVsActivityLog, qui peut être utilisée pour écrire au journal d’activité. Par exemple, voir [comment : Utilisez le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Voir aussi

- [Liste des services disponibles](../../extensibility/internals/list-of-available-services.md)
- [Utilisation et fourniture de services](../../extensibility/using-and-providing-services.md)
- [Conversions de casting et de type](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Cast](/cpp/cpp/casting)