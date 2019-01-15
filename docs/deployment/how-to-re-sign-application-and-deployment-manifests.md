---
title: 'Procédure : Signer à nouveau les manifestes de déploiement et d’Application | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5276f77226930b7ad49aea3253321ed3c8082be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937983"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Procédure : Resigner des manifestes d’application et de déploiement
Une fois que vous apportez des modifications aux propriétés de déploiement dans le manifeste d’application pour les applications Windows Forms, les applications Windows Presentation Foundation (xbap) ou les solutions Office, vous devez resigner l’application et les manifestes de déploiement avec un certificat. Ce processus aide à garantir que des fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Un autre scénario dans lequel vous pouvez signer à nouveau les manifestes est lorsque vos clients souhaitent signer l’application et manifestes de déploiement avec leur propre certificat.  
  
## <a name="re-sign-the-application-and-deployment-manifests"></a>Resigner les manifestes d’application et de déploiement  
 Cette procédure suppose que vous avez déjà modifié votre fichier manifeste d’application (*.manifest*). Pour plus d'informations, voir [Procédure : Modifier les propriétés de déploiement](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour signer à nouveau l’application et déploiement manifestes avec Mage.exe  
  
1.  Ouvrir un **invite de commandes Visual Studio** fenêtre.  
  
2.  Accédez au dossier qui contient les fichiers manifeste que vous souhaitez vous connecter.  
  
3.  Tapez la commande suivante pour signer le fichier manifeste d’application. Remplacez *ManifestFileName* avec le nom de votre fichier manifeste ainsi que l’extension. Remplacez *certificat* avec le chemin d’accès qualifié complet ou relatif du fichier de certificat et remplacez *mot de passe* avec le mot de passe pour le certificat.  
  
    ```cmd  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécutez la commande suivante pour signer un manifeste d’application pour un complément, une application Windows Form ou une application de navigateur Windows Presentation Foundation. Certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans les environnements de production.  
  
    ```cmd  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d’espace réservé, comme dans l’étape précédente.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourrez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Si vous le souhaitez, copiez le manifeste de déploiement principal (*publier\\\<appname > .application*) dans votre répertoire de déploiement de version (*publish\Application Files\\ \<appname > _\<version >*).  
  
## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Mettre à jour et signer à nouveau les manifestes d’application et de déploiement  
 Cette procédure suppose que vous avez déjà modifié votre fichier manifeste d’application (*.manifest*), mais que d’autres fichiers qui ont été mis à jour. Lorsque les fichiers sont mis à jour, le hachage qui représente le fichier doit également être mis à jour.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour mettre à jour et signer à nouveau l’application et déploiement manifestes avec Mage.exe  
  
1.  Ouvrir un **invite de commandes Visual Studio** fenêtre.  
  
2.  Accédez au dossier qui contient les fichiers manifeste que vous souhaitez vous connecter.  
  
3.  Supprimer le *.deploy* extension de fichier à partir des fichiers dans la publication dans le dossier de sortie.  
  
4.  Tapez la commande suivante pour mettre à jour le manifeste d’application avec les nouveaux hachages pour les fichiers mis à jour et signer le fichier manifeste d’application. Remplacez *ManifestFileName* avec le nom de votre fichier manifeste ainsi que l’extension. Remplacez *certificat* avec le chemin d’accès qualifié complet ou relatif du fichier de certificat et remplacez *mot de passe* avec le mot de passe pour le certificat.  
  
    ```cmd  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécutez la commande suivante pour signer un manifeste d’application pour un complément, une application Windows Form ou une application de navigateur Windows Presentation Foundation. Certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans les environnements de production.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d’espace réservé, comme dans l’étape précédente.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourrez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Ajouter le *.deploy* extension de fichier vers les fichiers, sauf les fichiers de manifeste de l’application et déploiement.  
  
7.  Si vous le souhaitez, copiez le manifeste de déploiement principal (*publier\\\<appname > .application*) dans votre répertoire de déploiement de version (*publish\Application Files\\ \<appname > _\<version >*).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [Guide pratique pour activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Guide pratique pour définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Guide pratique pour ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Guide pratique pour configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)