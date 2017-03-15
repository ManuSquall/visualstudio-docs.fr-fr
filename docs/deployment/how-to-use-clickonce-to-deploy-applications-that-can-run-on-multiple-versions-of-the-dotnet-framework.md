---
title: "How to: Use ClickOnce to Deploy Applications That Can Run on Multiple Versions of the .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce applications, multiple .NET Framework versions"
  - "ClickOnce deployment, multiple .NET Framework versions"
  - "deploying applications [ClickOnce], multiple .NET Framework versions"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Use ClickOnce to Deploy Applications That Can Run on Multiple Versions of the .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez déployer une application qui cible plusieurs versions de .NET Framework à l'aide de la technologie de déploiement ClickOnce.  Cela nécessite que vous génériez et mettiez à jour les manifestes de déploiement et d'application.  
  
> [!NOTE]
>  Avant de modifier l'application de façon à cibler plusieurs versions de .NET Framework, vous devez vous assurer que votre application peut s'exécuter avec plusieurs versions de .NET Framework.  Le common language runtime de version est différent entre [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] et .NET Framework 2.0, .NET Framework 3.0 et .NET Framework 3.5.  
  
 Ce processus implique les étapes suivantes :  
  
1.  Générer les manifestes d'application et de déploiement.  
  
2.  Modifier le manifeste de déploiement pour répertorier les différentes versions de .NET Framework.  
  
3.  Modifier le fichier app.config pour répertorier les versions du runtime .NET Framework compatibles.  
  
4.  Modifier le manifeste d'application pour marquer les assemblys dépendants en tant qu'assemblys .NET Framework.  
  
5.  Signer le manifeste d'application.  
  
6.  Mettre à jour et signer le manifeste de déploiement.  
  
### Pour générer les manifestes d'application et de déploiement  
  
-   Utilisez l'Assistant Publication ou la page Publier du Concepteur de projets pour publier l'application et générer les fichiers de manifeste de déploiement et d'application.  Pour plus d'informations, consultez [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md) ou [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md).  
  
### Pour modifier le manifeste de déploiement afin de répertorier les différentes versions de .NET Framework  
  
1.  Dans le répertoire de publication, ouvrez le manifeste de déploiement à l'aide de l'Éditeur XML dans Visual Studio.  Le manifeste de déploiement porte l'extension de nom de fichier .application.  
  
2.  Remplacez le code XML entre les éléments `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` et `</compatibleFrameworks>` par du code XML qui répertorie les versions de .NET Framework prises en charge par votre application.  
  
     Le tableau suivant affiche certaines des versions .NET Framework disponibles et le code XML correspondant que vous pouvez ajouter au manifeste de déploiement.  
  
    |Version du .NET Framework|XML|  
    |-------------------------------|---------|  
    |4 version de client|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 version complète|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 version de client|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 version complète|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### Pour modifier le fichier app.config afin de répertorier les versions compatibles du runtime .NET Framework  
  
1.  Dans l'Explorateur de solutions, ouvrez le fichier App.config à l'aide de l'Éditeur XML dans Visual Studio.  
  
2.  Remplacez \(ou ajoutez\) le code XML entre les éléments `<startup>` et `</startup>` par du code XML qui répertorie les runtimes de .NET Framework pris en charge par votre application.  
  
     Le tableau suivant affiche certaines des versions .NET Framework disponibles et le code XML correspondant que vous pouvez ajouter au manifeste de déploiement.  
  
    |Version du runtime .NET Framework|XML|  
    |---------------------------------------|---------|  
    |4 version de client|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 version complète|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 version complète|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 version de client|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### Pour modifier le manifeste d'application afin de marquer les assemblys dépendants en tant qu'assemblys .NET Framework  
  
1.  Dans le répertoire de publication, ouvrez le manifeste d'application à l'aide de l'Éditeur XML dans Visual Studio.  Le manifeste de déploiement porte l'extension de nom de fichier .manifest.  
  
2.  Ajoutez `group="framework"` à la dépendance XML pour les assemblys sentinel \(`System.Core`, `WindowsBase`, `Sentinel.v3.5Client` et `System.Data.Entity`\).  Par exemple, le code XML doit ressembler à ceci :  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Mettez à jour le numéro de version de l'élément `<assemblyIdentity>` pour Microsoft.Windows.CommonLanguageRuntime avec le numéro de version de .NET Framework qui est le plus petit dénominateur commun.  Par exemple, si l'application cible .NET Framework 3.5 et [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)], utilisez le numéro de version 2.0.50727.0 ; le code XML doit ressembler à ceci :  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### Pour mettre à jour et signer à nouveau les manifestes d'application et de déploiement  
  
-   Mettez à jour et signer à nouveau les manifestes d'application et de déploiement.  Pour plus d'informations, consultez [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Voir aussi  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> Element](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Schéma des fichiers de configuration](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)