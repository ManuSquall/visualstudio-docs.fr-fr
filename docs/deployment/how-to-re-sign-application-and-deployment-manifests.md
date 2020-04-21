---
title: 'Comment : Re-signer les manifestes d’application et de déploiement (fr) Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649185"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Guide pratique pour resigner des manifestes d’application et de déploiement
Après avoir apporté des modifications aux propriétés de déploiement dans le manifeste d’application pour les applications Windows Forms, les applications de la Fondation De présentation Windows (xbap) ou les solutions Office, vous devez re-signer à la fois l’application et le déploiement manifeste avec un certificat. Ce processus aide à garantir que des fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.

 Un autre scénario où vous pourriez re-signer les manifestes est lorsque vos clients veulent signer l’application et le déploiement manifeste avec leur propre certificat.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Resigner les manifestes d’application et de déploiement
 Cette procédure suppose que vous avez déjà apporté des modifications à votre fichier manifeste de demande (*.manifeste*). Pour plus d’informations, voir [Comment : Changer les propriétés de déploiement](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour re-signer l’application et le déploiement manifeste avec Mage.exe

1. Ouvrez une fenêtre **Visual Studio Command Prompt.**

2. Changez les répertoires dans le dossier qui contient les fichiers manifestes que vous souhaitez signer.

3. Tapez la commande suivante pour signer le fichier manifeste de l’application. Remplacez *ManifestFileName* par le nom de votre fichier manifeste plus l’extension. Remplacez *le certificat* par le chemin relatif ou entièrement qualifié du fichier de certificat et *remplacez Password* par le mot de passe pour le certificat.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Par exemple, vous pouvez exécuter la commande suivante pour signer un manifeste d’application pour un add-in, une application de formulaire Windows ou une application de navigateur de la Fondation de présentation Windows. Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans des environnements de production.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms des propriétaires de lieux comme dans l’étape précédente.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Par exemple, vous pouvez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un add-in Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Optionnellement, copiez le manifeste de déploiement principal *(publier\\\<le nom d’application>.application*) à votre répertoire de déploiement de version *(publier le nom d’application de fichiers\\\<>_\<version>*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Mettre à jour et re-signer l’application et le déploiement manifeste
 Cette procédure suppose que vous avez déjà apporté des modifications à votre fichier manifeste de demande (*.manifeste*), mais qu’il ya d’autres fichiers qui ont été mis à jour. Lorsque les fichiers sont mis à jour, le hachage qui représente le fichier doit également être mis à jour.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Pour mettre à jour et re-signer l’application et le déploiement manifeste avec Mage.exe

1. Ouvrez une fenêtre **Visual Studio Command Prompt.**

2. Changez les répertoires dans le dossier qui contient les fichiers manifestes que vous souhaitez signer.

3. Supprimer l’extension de fichier *.deploy* des fichiers dans le dossier de sortie de publication.

4. Tapez la commande suivante pour mettre à jour le manifeste de l’application avec les nouvelles hachages pour les fichiers mis à jour et signez le fichier manifeste de l’application. Remplacez *ManifestFileName* par le nom de votre fichier manifeste plus l’extension. Remplacez *le certificat* par le chemin relatif ou entièrement qualifié du fichier de certificat et *remplacez Password* par le mot de passe pour le certificat.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Par exemple, vous pouvez exécuter la commande suivante pour signer un manifeste d’application pour un add-in, une application de formulaire Windows ou une application de navigateur de la Fondation de présentation Windows. Les certificats temporaires créés par Visual Studio ne sont pas recommandés pour le déploiement dans des environnements de production.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Tapez la commande suivante pour mettre à jour et signer le fichier manifeste de déploiement, en remplaçant les noms des propriétaires de lieux comme dans l’étape précédente.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Par exemple, vous pouvez exécuter la commande suivante pour mettre à jour et signer un manifeste de déploiement pour un add-in Excel, une application Windows Forms ou une application de navigateur Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Ajoutez l’extension de fichier *.deploy* aux fichiers, à l’exception des fichiers manifestes d’application et de déploiement.

7. Optionnellement, copiez le manifeste de déploiement principal *(publier\\\<le nom d’application>.application*) à votre répertoire de déploiement de version *(publier le nom d’application de fichiers\\\<>_\<version>*).

## <a name="see-also"></a>Voir aussi
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)
- [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)
- [Guide pratique pour activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Comment : Définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](securing-clickonce-applications.md)
- [Guide pratique pour ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Guide pratique pour configurer le comportement de l’invite de l’approbation ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)