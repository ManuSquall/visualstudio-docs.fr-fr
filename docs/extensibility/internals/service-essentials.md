---
title: Notions fondamentales sur service | Microsoft Docs
description: En savoir plus sur les services, qui sont des interfaces à utiliser par un autre VSPackage. Les services d’un VSPackage peuvent remplacer des services intégrés ou d’autres services.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69e7e1c5b18019c4ff063ec504fc702f47f7e023
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080825"
---
# <a name="service-essentials"></a>Éléments fondamentaux du service
Un service est un contrat entre deux VSPackages. Un VSPackage fournit un ensemble spécifique d’interfaces à utiliser par un autre VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est lui-même une collection de VSPackages qui fournit des services à d’autres VSPackages.

 Par exemple, vous pouvez utiliser le service SVsActivityLog pour obtenir une interface IVsActivityLog, que vous pouvez utiliser pour écrire dans le journal d’activité. Pour plus d’informations, consultez [procédure : utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit également des services intégrés qui ne sont pas inscrits. Les VSPackages peuvent remplacer des services intégrés ou d’autres services en fournissant une substitution de service. Une seule substitution de service est autorisée pour n’importe quel service.

 Les services n’ont pas de détectabilité. Par conséquent, vous devez connaître l’identificateur de service (SID) d’un service que vous souhaitez utiliser, et vous devez connaître les interfaces qu’il fournit. La documentation de référence pour le service fournit ces informations.

- Les VSPackages qui fournissent des services sont appelés fournisseurs de services.

- Les services fournis à d’autres VSPackages sont appelés services globaux.

- Les services qui sont disponibles uniquement pour le VSPackage qui les implémente, ou pour tout objet qu’il crée, sont appelés services locaux.

- Les services qui remplacent les services intégrés ou les services fournis par d’autres packages sont appelés des substitutions de service.

- Les services, ou substitutions de service, sont chargés à la demande, autrement dit, le fournisseur de services est chargé lorsque le service qu’il fournit est demandé par un autre VSPackage.

- Pour prendre en charge le chargement à la demande, un fournisseur de services inscrit ses services globaux auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pour plus d’informations, consultez [Comment : fournir un service](../../extensibility/how-to-provide-a-service.md).

- Après avoir obtenu un service, utilisez [QueryInterface](/cpp/atl/queryinterface) (code non managé) ou une conversion (code managé) pour obtenir l’interface souhaitée, par exemple :

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Le code managé fait référence à un service par son type, alors que le code non managé fait référence à un service par son GUID.

- Lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge un VSPackage, il passe un fournisseur de services au VSPackage pour accorder l’accès au VSPackage aux services globaux. C’est ce que l’on appelle le VSPackage.

- Les VSPackages peuvent être des fournisseurs de services pour les objets qu’ils créent. Par exemple, un formulaire peut envoyer une demande de service de couleur à son Frame, qui peut passer la demande à [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Les objets managés qui sont profondément imbriqués, ou qui ne sont pas sur site, peuvent appeler <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> pour un accès direct aux services globaux.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Utiliser GetGlobalService

Parfois, vous devrez peut-être obtenir un service à partir d’une fenêtre outil ou d’un conteneur de contrôle qui n’a pas été sur site, ou avec un fournisseur de services qui ne connaît pas le service souhaité. Par exemple, vous souhaiterez peut-être écrire dans le journal d’activité à partir d’un contrôle. Pour plus d’informations sur ces scénarios et d’autres, consultez Guide pratique [pour résoudre les problèmes liés aux services](../../extensibility/how-to-troubleshoot-services.md).

Vous pouvez accéder à la plupart des services Visual Studio en appelant la <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> méthode statique.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> s’appuie sur un fournisseur de services mis en cache qui est initialisé la première fois qu’un VSPackage dérivé du package est placé dans un site. Vous devez vous assurer que cette condition est remplie ou être préparée pour un service null.

Heureusement, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> fonctionne bien la plupart du temps.

- Si un VSPackage fournit un service connu uniquement d’un autre VSPackage, le VSPackage qui demande le service est sur site avant le chargement du VSPackage.

- Si une fenêtre outil est créée par un VSPackage, le VSPackage est sur site avant la création de la fenêtre outil.

- Si un conteneur de contrôle est hébergé par une fenêtre outil créée par un VSPackage, le VSPackage est sur site avant que le conteneur de contrôle ne soit créé.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Pour obtenir un service à partir d’une fenêtre outil ou d’un conteneur de contrôle

- Insérez ce code dans le constructeur, la fenêtre outil ou le conteneur de contrôle :

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

    Ce code obtient un service SVsActivityLog et le convertit en une interface IVsActivityLog, qui peut être utilisée pour écrire dans le journal d’activité. Pour obtenir un exemple, consultez [procédure : utiliser le journal d’activité](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Voir aussi

- [Liste des services disponibles](../../extensibility/internals/list-of-available-services.md)
- [Utilisation et fourniture de services](../../extensibility/using-and-providing-services.md)
- [Cast et conversions de types](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Transtypage](/cpp/cpp/casting)
