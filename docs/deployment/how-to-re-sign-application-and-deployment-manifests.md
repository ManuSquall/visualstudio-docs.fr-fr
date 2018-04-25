---
title: 'Comment : signer de nouveau les manifestes de déploiement et d’Application | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba634ffb30d6459c940811f0ea080f8b71a37f34
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Comment : signer de nouveau des manifestes d'application et de déploiement
Une fois que vous apportez des modifications aux propriétés de déploiement dans le manifeste d’application pour les applications Windows Forms, les applications Windows Presentation Foundation (xbap) ou les solutions Office, vous devez signer de nouveau l’application et les manifestes de déploiement avec un certificat. Ce processus garantit que les fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Un autre scénario où vous pouvez signer à nouveau les manifestes est lorsque vos clients veulent signer l’application et les manifestes de déploiement avec leur propre certificat.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Manifestes de signer à nouveau l’Application et déploiement  
 Cette procédure suppose que vous avez déjà modifié votre fichier manifeste d’application (.manifest). Pour plus d’informations, consultez [Comment : modifier les propriétés de déploiement](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour signer à nouveau l’application et déploiement manifestes avec Mage.exe  
  
1.  Ouvrir un **invite de commandes Visual Studio** fenêtre.  
  
2.  Accédez au dossier qui contient les fichiers manifestes que vous voulez vous connecter.  
  
3.  Tapez la commande suivante pour signer le fichier manifeste d’application. Remplacez ManifestFileName par le nom de votre fichier manifeste ainsi que l’extension. Remplacez le certificat avec le chemin d’accès qualifié complet ou relatif du fichier de certificat et mot de passe avec le mot de passe pour le certificat.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour signer un manifeste d’application pour un complément, une application Windows Form ou une application de navigateur Windows Presentation Foundation. Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans les environnements de production.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d’espace réservé comme dans l’étape précédente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Si vous le souhaitez, copiez le manifeste de déploiement principal (publier\\*appname*.application) dans le répertoire de déploiement de votre version (publish\Application Files\\*appname*_ *version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Mise à jour et signer à nouveau l’Application et les manifestes de déploiement  
 Cette procédure suppose que vous avez déjà effectué des modifications de votre application (.manifest) de fichier manifeste, mais qu’il existe d’autres fichiers qui ont été mis à jour. Lorsque les fichiers sont mis à jour, le hachage qui représente le fichier doit également être mis à jour.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour mettre à jour et signer à nouveau l’application et déploiement manifestes avec Mage.exe  
  
1.  Ouvrir un **invite de commandes Visual Studio** fenêtre.  
  
2.  Accédez au dossier qui contient les fichiers manifestes que vous voulez vous connecter.  
  
3.  Supprimez l’extension de fichier .deploy à partir des fichiers dans le dossier de sortie de publication.  
  
4.  Tapez la commande suivante pour mettre à jour le manifeste d’application avec les nouveaux hachages pour les fichiers mis à jour et signer le fichier manifeste d’application. Remplacez ManifestFileName par le nom de votre fichier manifeste ainsi que l’extension. Remplacez le certificat avec le chemin d’accès qualifié complet ou relatif du fichier de certificat et mot de passe avec le mot de passe pour le certificat.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour signer un manifeste d’application pour un complément, une application Windows Form ou une application de navigateur Windows Presentation Foundation. Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans les environnements de production.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms d’espace réservé comme dans l’étape précédente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un complément Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Ajouter l’extension de fichier .deploy vers les fichiers, sauf les fichiers manifeste de l’application et déploiement.  
  
7.  Si vous le souhaitez, copiez le manifeste de déploiement principal (publier\\*appname*.application) dans le répertoire de déploiement de votre version (publish\Application Files\\*appname*_ *version*).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [Guide pratique pour activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Guide pratique pour définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Comment : ajouter un éditeur approuvé à un ordinateur Client pour les Applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Guide pratique pour configurer le comportement de l’invite d’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)