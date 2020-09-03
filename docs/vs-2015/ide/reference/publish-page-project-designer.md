---
title: Page Publier, Concepteur de projets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665704"
---
# <a name="publish-page-project-designer"></a>Page Publier, Concepteur de projets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La page **Publier** du **Concepteur de projets** permet de configurer les propriétés du déploiement ClickOnce.

 Pour accéder à la boîte de dialogue **Publier** , sélectionnez un nœud de projet dans l’ **Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Publier** .

> [!NOTE]
> Certaines des propriétés ClickOnce décrites ici peuvent également être définies dans **l’Assistant Publication**, accessible à partir du menu **Générer** ou en cliquant sur le bouton **Assistant Publication** dans cette page.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Emplacement du dossier de publication** Spécifie l’emplacement où l’application est publiée. Peut être un chemin de lecteur (`C:\deploy\myapplication`), un partage de fichiers (`\\server\myapplication`), un serveur FTP (`ftp://ftp.microsoft.com/myapplication`) ou un site web (`http://www.microsoft.com/myapplication`). Notez que du texte doit figurer dans la zone **Emplacement de publication** pour que le bouton de navigation (**...**) fonctionne.

 Par défaut, l’emplacement de publication est `http://localhost/<projectname>/` si vous avez installé IIS, ou le répertoire `publish\` si vous n’avez pas installé IIS. Si votre ordinateur exécute Windows Vista, la valeur par défaut est toujours le répertoire `publish\` , qu’IIS soit installé ou non.

 **URL du dossier d’installation** Facultatif. Spécifie un site web auquel les utilisateurs accèdent pour installer l’application. Cette URL est nécessaire uniquement si elle diffère de l’ **Emplacement de publication**, par exemple quand l’application est publiée sur un serveur intermédiaire.

 **Mode et paramètres d’installation** Détermine si l’application est exécutée directement à partir de l' **emplacement de publication** (quand **l’option l’application est disponible en ligne uniquement** est sélectionnée) ou si elle est installée et ajoutée au menu **Démarrer** et à l’élément **Ajout/suppression de programmes** du **panneau de configuration** (quand **l’option l’application est également disponible hors connexion** est sélectionnée).

 Pour les applications du navigateur web WPF, l’option **L’application est également disponible hors connexion** est désactivée, car ces applications sont disponibles uniquement en ligne.

 **Fichiers d’application** Ouvre la [boîte de dialogue fichiers d’application](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), qui permet de spécifier comment et où les fichiers sont installés.

 **Conditions préalables** Ouvre la [boîte de dialogue composants requis](../../ide/reference/prerequisites-dialog-box.md), qui permet de spécifier les composants requis, tels que le .NET Framework, à installer avec l’application.

 **Mises à jour** Ouvre la [boîte de dialogue mises à jour des applications](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), qui permet de spécifier le comportement de mise à jour pour l’application. Non disponible quand l’option **L’application est disponible en ligne uniquement** est sélectionnée.

 **Options** Ouvre la [boîte de dialogue Options de publication](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), qui permet de spécifier des options de publication avancées supplémentaires.

 **Version de publication** Définit le numéro de version de publication de l’application ; Lorsque le numéro de version est modifié, l’application est publiée en tant que mise à jour. Chaque partie de la version de publication (**Principale**, **Secondaire**, **Build**, **Révision**) peut avoir une valeur maximale de 65355 (<xref:System.UInt16.MaxValue>), la valeur maximale autorisée par <xref:System.Version>.

 Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.

 **Incrémenter automatiquement la révision avec chaque publication** Facultatif. Quand cette option est activée (valeur par défaut), la partie **Révision** du numéro de version de publication est incrémentée d’une unité chaque fois que l’application est publiée. Cela entraîne la publication de l’application en tant que mise à jour.

 **Assistant Publication** Ouvre l' [Assistant Publication](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). L’exécution complète de l’Assistant Publication a le même effet que l’exécution de la commande **Publier** dans le menu **Générer** .

 **Publier maintenant** Publie l’application à l’aide des paramètres actuels. Équivaut au bouton **Terminer** situé dans **l’Assistant Publication**.

## <a name="see-also"></a>Voir aussi
 [Publication d’applications ClickOnce](../../deployment/publishing-clickonce-applications.md) [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) [Comment : spécifier l’endroit où Visual Studio copie les fichiers](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md) [Comment : spécifier l’emplacement où les utilisateurs finaux seront installés à partir de](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md) [Comment : spécifier un lien pour le support technique](../../deployment/how-to-specify-a-link-for-technical-support.md) Comment : spécifier le [mode d’installation en ligne ou hors connexion ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md) Comment : [activer le démarrage automatique pour les installations de CD-ROM](../../deployment/how-to-enable-autostart-for-cd-installations.md) [Comment : définir la version de publication ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md) [Comment : incrémenter automatiquement la version de publication ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) [Comment : spécifier les fichiers publiés par ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md) [Comment : installer les composants requis avec une application ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [Comment : gérer les mises à jour pour une application ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md) [Comment : modifier la langue de publication pour une](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md) application ClickOnce Comment : [spécifier un nom de menu Démarrer pour une application ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) [Comment : : Spécifier une page de publication pour une application ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) [sécurité et déploiement ClickOnce](../../deployment/clickonce-security-and-deployment.md)
