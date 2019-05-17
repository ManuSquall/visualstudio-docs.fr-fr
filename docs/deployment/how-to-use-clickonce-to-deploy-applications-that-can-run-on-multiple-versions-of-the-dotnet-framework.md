---
title: 'Procédure : Utiliser ClickOnce pour déployer des Applications pouvant s’exécuter sur plusieurs Versions du .NET Framework | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e7e7d79dd1fc3d6c988701d0aa88cb4d0d299c2d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406723"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Procédure : Utiliser ClickOnce pour déployer des applications pouvant s’exécuter sur plusieurs versions du .NET Framework
Vous pouvez déployer une application qui cible plusieurs versions du .NET Framework à l’aide de la technologie de déploiement ClickOnce. Cela nécessite que vous générez et mettre à jour les manifestes d’application et de déploiement.

> [!NOTE]
> Avant de modifier l’application pour cibler plusieurs versions du .NET Framework, vous devez vous assurer que votre application s’exécute avec plusieurs versions du .NET Framework. Le common language runtime de version est différent entre [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] et .NET Framework 2.0, .NET Framework 3.0 et .NET Framework 3.5.

 Ce processus implique les étapes suivantes :

1. Générer les manifestes d’application et de déploiement.

2. Modifier le manifeste de déploiement pour répertorier les différentes versions de .NET Framework.

3. Modifier le *app.config* fichier pour répertorier les versions du runtime compatibles .NET Framework.

4. Modifier le manifeste d’application pour marquer les assemblys dépendants en tant qu’assemblys .NET Framework.

5. Signer le manifeste d’application.

6. Mettre à jour et signer le manifeste de déploiement.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Pour générer les manifestes d’application et de déploiement

- Utilisez l’Assistant Publication ou la Page Publier du Concepteur de projets pour publier l’application et de générer l’application et les fichiers manifeste de déploiement. Pour plus d'informations, voir [Procédure : Publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) ou [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Pour modifier le manifeste de déploiement pour répertorier les différentes versions de .NET Framework

1. Dans le répertoire de publication, ouvrez le manifeste de déploiement à l’aide de l’éditeur XML dans Visual Studio. Le manifeste de déploiement a la *.application* extension de nom de fichier.

2. Remplacez le code XML entre les `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` et `</compatibleFrameworks>` éléments XML qui répertorie les versions de .NET Framework prises en charge pour votre application.

     Le tableau suivant présente certaines des versions du .NET Framework disponibles et le schéma XML correspondant que vous pouvez ajouter au manifeste de déploiement.

    |Version du .NET Framework|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Pour modifier le fichier app.config pour répertorier les versions du runtime compatibles .NET Framework

1. Dans l’Explorateur de solutions, ouvrez le *app.config* fichier à l’aide de l’éditeur XML dans Visual Studio.

2. Remplacez (ou ajoutez) le code XML entre les `<startup>` et `</startup>` éléments XML qui répertorie les runtimes pris en charge de .NET Framework pour votre application.

     Le tableau suivant présente certaines des versions du .NET Framework disponibles et le schéma XML correspondant que vous pouvez ajouter au manifeste de déploiement.

    |Version du runtime .NET framework|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Pour modifier le manifeste d’application pour marquer les assemblys dépendants en tant qu’assemblys .NET Framework

1. Dans le répertoire de publication, ouvrez le manifeste d’application à l’aide de l’éditeur XML dans Visual Studio. Le manifeste de déploiement a la *.manifest* extension de nom de fichier.

2. Ajouter `group="framework"` à la dépendance XML pour les assemblys sentinel (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, et `System.Data.Entity`). Par exemple, le code XML doit ressembler à ce qui suit :

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Mettre à jour le numéro de version de la `<assemblyIdentity>` élément pour Microsoft.Windows.CommonLanguageRuntime avec le numéro de version pour le .NET Framework qui est le plus petit dénominateur commun. Par exemple, si l’application cible .NET Framework 3.5 et [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], utilisez la version numéro 2.0.50727.0 et le code XML doivent ressembler à ce qui suit :

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Pour mettre à jour et signer à nouveau l’application et déploiement de manifestes

- Mettre à jour et signer à nouveau les manifestes d’application et de déploiement. Pour plus d'informations, voir [Procédure : Resigner des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks > élément](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dépendance > élément](../deployment/dependency-element-clickonce-application.md)
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Schéma des fichiers de configuration](/dotnet/framework/configure-apps/file-schema/index)