---
title: Service Essentials | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e867c9e83bf353e57d75ee611fe1074efcc9cfe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070379"
---
# <a name="service-essentials"></a>Éléments fondamentaux du service
Un service est un contrat entre deux VSPackages. Un VSPackage fournit un ensemble spécifique d’interfaces pour un autre package Visual Studio consommer. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est lui-même une collection de VSPackages qui fournit des services aux autres VSPackages.

 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire dans le journal d’activité. Pour plus d'informations, voir [Procédure : Utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit également des services intégrés qui ne sont pas enregistrées. VSPackages peut remplacer intégrés ou d’autres services en fournissant un service de remplacement. Remplacement d’un seul service est autorisée pour n’importe quel service.

 Les services n’ont aucune fonctionnalité de découverte. Par conséquent, vous devez connaître l’identificateur de service (SID) d’un service que vous souhaitez utiliser, et vous devez connaître les interfaces qu’il fournit. La documentation de référence pour le service fournit ces informations.

- Les VSPackages qui fournissent des services sont appelés fournisseurs de services.

- Les services fournis aux autres packages VS sont appelés des services globaux.

- Les services qui sont disponibles uniquement pour le VSPackage qui implémente les, ou pour tout objet qu’elle crée, sont appelés des services locaux.

- Les services qui remplacent les services intégrés ou des services fournis par d’autres packages, sont appelés des remplacements de service.

- Services ou les remplacements de service, sont chargées à la demande, autrement dit, le fournisseur de services est chargé lorsque le service qu’il fournit est demandé par un autre package Visual Studio.

- Pour prendre en charge le chargement à la demande, un fournisseur de services enregistre ses services globaux auprès [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pour plus d'informations, voir [Procédure : Fournir un Service](../../extensibility/how-to-provide-a-service.md).

- Après avoir obtenu un service, utilisez [QueryInterface](/cpp/atl/queryinterface) (code non managé) ou d’un transtypage (code managé) pour obtenir l’interface souhaitée, par exemple :

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Le code managé fait référence à un service par son type, tandis que le code non managé fait référence à un service par son GUID.

- Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge un VSPackage, il transmet un fournisseur de services au VSPackage pour accorder l’accès de package Visual Studio pour les services globaux. Cela est appelé « positionnement » le VSPackage.

- Les VSPackages peuvent être des fournisseurs de services pour les objets qu’ils créent. Par exemple, un formulaire peut envoyer une demande pour un service de couleur à son image, qui peut transmettre la requête [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Objets managés qui sont profondément imbriquées ou pas du tout, doit se trouver peuvent appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour accéder directement aux services globaux.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Utilisation d’un GetGlobalService

Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou le contrôle conteneur qui n’a pas été installé, ou bien a été installé avec un fournisseur de services qui ne sait pas sur le service que vous souhaitez. Par exemple, vous souhaiterez peut-être écrire dans le journal d’activité à partir d’un contrôle. Pour plus d’informations sur ces scénarios et d’autres, consultez [Comment : Dépanner les Services](../../extensibility/how-to-troubleshoot-services.md).

Vous pouvez obtenir la plupart des services de Visual Studio en appelant la méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (méthode).

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> s’appuie sur un service de mise en cache le fournisseur qui est initialisé à la première fois qu’un VSPackage dérivé de Package est placé. Vous devez vous assurer que cette condition est remplie, ou bien être préparée pour un service de type null.

Heureusement, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> fonctionne correctement la plupart du temps.

- Si un VSPackage fournit un service connu uniquement à un autre package Visual Studio, le VSPackage demandant le service est placé avant le VSPackage pour fournir que le service est chargé.

- Si une fenêtre outil est créée par un VSPackage, le VSPackage est placé avant la création de la fenêtre outil.

- Si un conteneur de contrôle est hébergé par une fenêtre outil créée par un VSPackage, le VSPackage est placé avant le conteneur de contrôle est créé.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Pour obtenir un service à partir d’un conteneur de contrôle ou de la fenêtre outil

- Insérez ce code dans le constructeur, une fenêtre outil ou un conteneur de contrôle :

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

    Ce code obtient un service SVsActivityLog et il effectue un cast en interface IVsActivityLog, qui peut être utilisée pour écrire dans le journal d’activité. Pour voir un exemple, consultez [Comment : Utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Voir aussi

- [Liste des services disponibles](../../extensibility/internals/list-of-available-services.md)
- [Utilisation et fourniture de services](../../extensibility/using-and-providing-services.md)
- [Cast et conversions de types](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Cast](/cpp/cpp/casting)