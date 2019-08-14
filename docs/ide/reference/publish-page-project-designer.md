---
title: Page Publier, Concepteur de projets
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbb43408dc12c55b72eb0ca0909d8b261198a5b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926171"
---
# <a name="publish-page-project-designer"></a>Page Publier, Concepteur de projets

La page **Publier** du **Concepteur de projets** permet de configurer les propriétés du déploiement ClickOnce.

Pour accéder à la boîte de dialogue **Publier** , sélectionnez un nœud de projet dans l’ **Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Publier** .

> [!NOTE]
> Certaines des propriétés ClickOnce décrites ici peuvent également être définies dans **l’Assistant Publication**, accessible à partir du menu **Générer** ou en cliquant sur le bouton **Assistant Publication** dans cette page.

## <a name="uielement-list"></a>Liste des éléments d’interface

 **Emplacement du dossier de publication**

Spécifie l’emplacement où l’application est publiée. Peut être un chemin de lecteur (`C:\deploy\myapplication`), un partage de fichiers (`\\server\myapplication`) ou un serveur FTP (`ftp://ftp.microsoft.com/myapplication`). Notez que du texte doit figurer dans la zone **Emplacement de publication** pour que le bouton de navigation ( **...** ) fonctionne.

 **URL du dossier d'installation**

facultatif. Spécifie un site web auquel les utilisateurs accèdent pour installer l’application. Cette URL est nécessaire uniquement si elle diffère de l’ **Emplacement de publication**, par exemple quand l’application est publiée sur un serveur intermédiaire.

 **Mode et paramètres d'installation**

Détermine si l’application est exécutée directement à partir de l’ **Emplacement de publication** (quand l’option **L’application est disponible en ligne uniquement** est sélectionnée) ou si elle est installée et ajoutée au menu **Démarrer** et à l’élément **Ajouter ou supprimer des programmes** du **Panneau de configuration** (quand l’option **L’application est également disponible hors connexion** est sélectionnée).

Pour les applications du navigateur web WPF, l’option **L’application est également disponible hors connexion** est désactivée, car ces applications sont disponibles uniquement en ligne.

 **Fichiers de l’application**

Ouvre la boîte de dialogue Fichiers d’application, qui permet de spécifier comment et où les fichiers sont installés.

 **Composants requis**

Ouvre la boîte de dialogue Composants requis, qui permet de spécifier les composants requis, tels que le .NET Framework, à installer avec l’application.

 **Mises à jour**

Ouvre la boîte de dialogue Mise à jour des applications, qui permet de spécifier le comportement de mise à jour de l’application. Non disponible quand l’option **L’application est disponible en ligne uniquement** est sélectionnée.

 **Options**

Ouvre la boîte de dialogue Options de publication, qui permet de spécifier des options de publication avancées.

 **Version de publication**

Définit le numéro de version de publication de l’application. Quand vous changez le numéro de version, l’application est publiée en tant que mise à jour. Chaque partie de la version de publication (**Principale**, **Secondaire**, **Build**, **Révision**) peut avoir une valeur maximale de 65355 (<xref:System.UInt16.MaxValue>), la valeur maximale autorisée par <xref:System.Version>.

Quand vous installez plusieurs versions d'une application via ClickOnce, l'installation déplace les versions antérieures de cette application dans un dossier nommé Archive, à l'emplacement de publication que vous avez spécifié. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.

 **Incrémenter automatiquement la révision avec chaque publication**

facultatif. Quand cette option est activée (valeur par défaut), la partie **Révision** du numéro de version de publication est incrémentée d’une unité chaque fois que l’application est publiée. Cela entraîne la publication de l’application en tant que mise à jour.

 **Assistant Publication**

Ouvre l’Assistant Publication. L’exécution complète de l’Assistant Publication a le même effet que l’exécution de la commande **Publier** dans le menu **Générer** .

 **Publier maintenant**

Publie l’application à l’aide des paramètres actuels. Équivaut au bouton **Terminer** situé dans **l’Assistant Publication**.

## <a name="see-also"></a>Voir aussi

- [Publication d’applications ClickOnce](../../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Guide pratique pour spécifier l’endroit où Visual Studio copie les fichiers](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Guide pratique pour spécifier l’emplacement à partir duquel les utilisateurs finaux effectuent l’installation](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Guide pratique pour spécifier un lien pour le support technique](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Guide pratique pour spécifier le mode d’installation en ligne ou hors connexion de ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Guide pratique pour activer le démarrage automatique pour les installations depuis un CD-ROM](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Guide pratique pour définir la version de publication ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Guide pratique pour incrémenter automatiquement la version de publication ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Guide pratique pour spécifier les fichiers publiés par ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Guide pratique pour installer des prérequis avec une application ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Guide pratique pour gérer les mises à jour d’une application ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Guide pratique pour changer la langue de publication d’une application ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Guide pratique pour spécifier un nom de menu Démarrer pour une application ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Guide pratique pour spécifier une page de publication pour une application ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [Sécurité et déploiement ClickOnce](../../deployment/clickonce-security-and-deployment.md)
