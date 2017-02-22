---
title: "How to: Re-sign Application and Deployment Manifests | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Office applications, signing manifests"
  - "deploying applications [ClickOnce], signing manifests"
  - "deploying applications, signing manifests"
  - "ClickOnce deployment, signing manifests"
  - "Office development in Visual Studio, signing manifests"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# How to: Re-sign Application and Deployment Manifests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Après avoir apporté des modifications aux propriétés de déploiement dans le manifeste de l'application pour les applications Windows Forms, les applications Windows Presentation Foundation \(xbap\) ou les solutions Office, vous devez signer de nouveau les manifestes d'application et de déploiement avec un certificat.  Ce processus aide à garantir que les fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Il existe un autre scénario illustrant le besoin de signer de nouveau les manifestes : c'est lorsque vos clients souhaitent signer les manifestes d'application et de déploiement avec leur propre certificat.  
  
## Signer à nouveau les manifestes d'application et de déploiement  
 Cette procédure suppose que vous avez déjà apporté des modifications à votre fichier de manifeste d'application \(.manifest\).  Pour plus d'informations, consultez [Comment : modifier des propriétés de déploiement](http://msdn.microsoft.com/fr-fr/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### Pour signer à nouveau les manifestes d'application et de déploiement avec Mage.exe  
  
1.  Ouvrez une fenêtre **Invite de commandes de Visual Studio**.  
  
2.  Modifiez les répertoires en fonction du dossier qui contient les fichiers manifeste que vous souhaitez signer.  
  
3.  Tapez la commande suivante pour signer le fichier manifeste d'application.  Remplacez ManifestFileName par le nom de votre fichier manifeste ainsi que l'extension.  Remplacez Certificate par le chemin d'accès qualifié relatif ou complet du fichier de certificat et remplacez Password par le mot de passe du certificat.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour signer un manifeste d'application pour un complément, une application Windows Form ou une application de navigation Windows Presentation Foundation.  Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans des environnements de production.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d'espace réservé comme dans l'étape précédente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigation Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Vous pouvez également copier le manifeste de déploiement principal \(publish\\*nomapp*.application\) dans le répertoire de déploiement de votre version \(publish\\Application Files\\*nomapp*\_*version*\).  
  
## Mise à jour et nouvelle signature des manifestes d'application et de déploiement  
 Cette procédure suppose que vous avez déjà apporté des modifications à votre fichier manifeste d'application \(.manifest\), mais que d'autres fichiers ont été mis à jour.  Lorsque des fichiers sont mis à jour, le hachage qui représente le fichier doit également être mis à jour.  
  
#### Pour mettre à jour et signer à nouveau les manifestes d'application et de déploiement avec Mage.exe  
  
1.  Ouvrez une fenêtre **Invite de commandes de Visual Studio**.  
  
2.  Modifiez les répertoires en fonction du dossier qui contient les fichiers manifeste que vous souhaitez signer.  
  
3.  Supprimez l'extension de fichier .deploy dans les fichiers du dossier de sortie de publication.  
  
4.  Tapez la commande suivante pour mettre à jour le manifeste de l'application avec les nouveaux hachages destinés aux fichiers mis à jour et signez le fichier manifeste de l'application.  Remplacez ManifestFileName par le nom de votre fichier manifeste ainsi que l'extension.  Remplacez Certificate par le chemin d'accès qualifié relatif ou complet du fichier de certificat et remplacez Password par le mot de passe du certificat.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour signer un manifeste d'application pour un complément, une application Windows Form ou une application de navigation Windows Presentation Foundation.  Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans des environnements de production.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d'espace réservé comme dans l'étape précédente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigation Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Ajoutez à nouveau l'extension de fichier .deploy aux fichiers, à l'exception des fichiers manifeste de déploiement et d'application.  
  
7.  Vous pouvez également copier le manifeste de déploiement principal \(publish\\*nomapp*.application\) dans le répertoire de déploiement de votre version \(publish\\Application Files\\*nomapp*\_*version*\).  
  
## Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Comment : définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Comment : définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Comment : ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)