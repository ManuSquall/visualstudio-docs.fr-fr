---
title: 'Comment : signer à nouveau les manifestes d’application et de déploiement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697562"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Comment : signer de nouveau des manifestes d'application et de déploiement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Après avoir apporté des modifications aux propriétés de déploiement dans le manifeste d’application pour les applications Windows Forms, les applications Windows Presentation Foundation (XBAP) ou les solutions Office, vous devez signer à nouveau les manifestes d’application et de déploiement avec un certificat. Ce processus aide à garantir que des fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Un autre scénario dans lequel vous pouvez signer à nouveau les manifestes est lorsque vos clients souhaitent signer les manifestes d’application et de déploiement avec leur propre certificat.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Nouvelle signature des manifestes d’application et de déploiement  
 Cette procédure suppose que vous avez déjà apporté des modifications à votre fichier de manifeste d’application (. manifest). Pour plus d’informations, consultez [Comment : modifier les propriétés de déploiement](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour signer à nouveau les manifestes d’application et de déploiement avec Mage.exe  
  
1. Ouvrez une fenêtre d' **invite de commandes Visual Studio** .  
  
2. Remplacez les répertoires par le dossier qui contient les fichiers manifeste que vous souhaitez signer.  
  
3. Tapez la commande suivante pour signer le fichier manifeste de l’application. Remplacez ManifestFileName par le nom de votre fichier manifeste plus l’extension. Remplacez le certificat par le chemin d’accès relatif ou complet du fichier de certificat et remplacez Password par le mot de passe du certificat.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécuter la commande suivante pour signer un manifeste d’application pour un complément, une application Windows Form ou une application de navigateur Windows Presentation Foundation. Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans des environnements de production.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d’espaces réservés comme à l’étape précédente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Vous pouvez également copier le manifeste de déploiement principal (publier \\ *appname*. application) dans votre répertoire de déploiement de version (publish\Application Files \\ *appname*_*version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Mise à jour et nouvelle signature des manifestes d’application et de déploiement  
 Cette procédure suppose que vous avez déjà apporté des modifications à votre fichier de manifeste d’application (. manifest), mais que d’autres fichiers ont été mis à jour. Lorsque les fichiers sont mis à jour, le hachage qui représente le fichier doit également être mis à jour.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour mettre à jour et signer à nouveau les manifestes d’application et de déploiement avec Mage.exe  
  
1. Ouvrez une fenêtre d' **invite de commandes Visual Studio** .  
  
2. Remplacez les répertoires par le dossier qui contient les fichiers manifeste que vous souhaitez signer.  
  
3. Supprimez l’extension de fichier. deploy des fichiers dans le dossier de sortie de publication.  
  
4. Tapez la commande suivante pour mettre à jour le manifeste d’application avec les nouveaux hachages pour les fichiers mis à jour et signez le fichier manifeste de l’application. Remplacez ManifestFileName par le nom de votre fichier manifeste plus l’extension. Remplacez le certificat par le chemin d’accès relatif ou complet du fichier de certificat et remplacez Password par le mot de passe du certificat.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécuter la commande suivante pour signer un manifeste d’application pour un complément, une application Windows Form ou une application de navigateur Windows Presentation Foundation. Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans des environnements de production.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d’espaces réservés comme à l’étape précédente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pouvez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Rajoutez l’extension de fichier. deploy aux fichiers, à l’exception des fichiers de manifeste de déploiement et d’application.  
  
7. Vous pouvez également copier le manifeste de déploiement principal (publier \\ *appname*. application) dans votre répertoire de déploiement de version (publish\Application Files \\ *appname*_*version*).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [Comment : activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Comment : définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Comment : définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procédure : ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Comment : configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
