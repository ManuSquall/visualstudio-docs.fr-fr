---
title: Utiliser ClickOnce pour déployer des applications multicibles
description: Découvrez comment déployer une application qui cible plusieurs versions du .NET Framework à l’aide de la technologie de déploiement ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 67dcee1fac0b5ec082a7f92285c6c0ac2523800a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349514"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Guide pratique pour utiliser ClickOnce pour déployer des applications pouvant s’exécuter sur plusieurs versions du .NET Framework
Vous pouvez déployer une application qui cible plusieurs versions du .NET Framework à l’aide de la technologie de déploiement ClickOnce. Pour cela, vous devez générer et mettre à jour les manifestes d’application et de déploiement.

> [!NOTE]
> Avant de modifier l’application pour cibler plusieurs versions du .NET Framework, vous devez vous assurer que votre application s’exécute avec plusieurs versions du .NET Framework. La common language runtime de version est différente entre .NET Framework 4 et .NET Framework 2,0, .NET Framework 3,0 et .NET Framework 3,5.

 Ce processus implique les étapes suivantes :

1. Générez les manifestes d’application et de déploiement.

2. Modifiez le manifeste de déploiement pour répertorier les différentes versions de .NET Framework.

3. Modifiez le fichier *app.config* pour répertorier les versions du Runtime .NET Framework compatibles.

4. Modifiez le manifeste d’application pour marquer les assemblys dépendants comme des assemblys .NET Framework.

5. Signez le manifeste de l’application.

6. Mettez à jour et signez le manifeste de déploiement.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Pour générer les manifestes d’application et de déploiement

- Utilisez l’Assistant publication ou la page publier du concepteur de projet pour publier l’application et générer les fichiers de manifeste de l’application et du déploiement. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) ou de la [page publier du concepteur de projets](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>Pour modifier le manifeste de déploiement de façon à répertorier les différentes versions de .NET Framework

1. Dans le répertoire de publication, ouvrez le manifeste de déploiement à l’aide de l’éditeur XML dans Visual Studio. Le manifeste de déploiement a l’extension de nom de fichier *. application* .

2. Remplacez le code XML entre les `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` `</compatibleFrameworks>` éléments et par XML, qui répertorie les versions de .NET Framework prises en charge pour votre application.

     Le tableau suivant répertorie quelques-unes des versions .NET Framework disponibles et les données XML correspondantes que vous pouvez ajouter au manifeste de déploiement.

    |Version du .NET Framework|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>Pour modifier le fichier app.config afin de répertorier les versions du Runtime .NET Framework compatibles

1. Dans Explorateur de solutions, ouvrez le fichier *app.config* à l’aide de l’éditeur XML dans Visual Studio.

2. Remplacez (ou ajoutez) le code XML entre les `<startup>` `</startup>` éléments et par XML, qui répertorie les runtimes de .NET Framework pris en charge pour votre application.

     Le tableau suivant répertorie quelques-unes des versions .NET Framework disponibles et les données XML correspondantes que vous pouvez ajouter au manifeste de déploiement.

    |Version du Runtime .NET Framework|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>Pour modifier le manifeste d’application afin de marquer les assemblys dépendants comme des assemblys .NET Framework

1. Dans le répertoire de publication, ouvrez le manifeste d’application à l’aide de l’éditeur XML dans Visual Studio. Le manifeste de déploiement a l’extension de nom de fichier *. manifest* .

2. Ajoutez `group="framework"` au XML de dépendances pour les assemblys Sentinel ( `System.Core` , `WindowsBase` , `Sentinel.v3.5Client` et `System.Data.Entity` ). Par exemple, le code XML doit ressembler à ce qui suit :

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Mettez à jour le numéro de version de l' `<assemblyIdentity>` élément pour Microsoft. Windows. CommonLanguageRuntime en indiquant le numéro de version du .NET Framework qui est le plus petit dénominateur commun. Par exemple, si l’application cible .NET Framework 3,5 et .NET Framework 4, utilisez le numéro de version 2.0.50727.0 et le code XML doit ressembler à ce qui suit :

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Pour mettre à jour et signer à nouveau les manifestes d’application et de déploiement

- Mettez à jour et signez à nouveau les manifestes d’application et de déploiement. Pour plus d’informations, consultez [Comment : signer à nouveau les manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks> appartient](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dependency> appartient](../deployment/dependency-element-clickonce-application.md)
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Schéma des fichiers de configuration](/dotnet/framework/configure-apps/file-schema/index)
