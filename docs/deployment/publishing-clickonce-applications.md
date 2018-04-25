---
title: Publication d’Applications ClickOnce | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5f0c04a23844664b5bbfa67a6e83809c250b8a9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="publishing-clickonce-applications"></a>Publication d'applications ClickOnce
Lorsque vous publiez une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pour la première fois, les propriétés de publication peuvent être définies à l'aide de l'Assistant Publication. Seules quelques-unes des propriétés sont disponibles dans l'Assistant ; toutes les autres sont définies à leurs valeurs par défaut.  
  
 Les modifications ultérieures apportées aux propriétés de publication sont effectuées sur le **publier** page dans le **Concepteur de projet**.  
  
## <a name="publish-wizard"></a>Assistant Publication  
 Vous pouvez utiliser l'Assistant Publication pour définir les paramètres de base de la publication de votre application. Cette définition inclut les propriétés de publication suivantes :  
  
-   Emplacement du dossier de publication : endroit où Visual Studio copie les fichiers (ordinateur local, partage de fichiers réseau, serveur FTP ou site web)  
  
-   Emplacement du dossier d'installation : endroit à partir duquel les utilisateurs finaux installent (partage de fichiers réseau, serveur FTP, site web, CD/DVD)  
  
-   Disponibilité en ligne ou hors connexion : indique si les utilisateurs finaux peuvent accéder à l'application avec ou sans connexion réseau  
  
-   Fréquence des mises à jour : fréquence à laquelle l'application vérifie la présence de nouvelles mises à jour.  
  
 Pour plus d’informations, consultez [Comment : publier une Application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Page Publier  
 La page **Publier** du **Concepteur de projets** permet de configurer les propriétés du déploiement ClickOnce. Le tableau suivant répertorie les rubriques.  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour spécifier l’endroit où Visual Studio copie les fichiers](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Décrit comment définir l'emplacement où Visual Studio place les fichiers d'application et les manifestes.|  
|[Guide pratique pour spécifier l’emplacement à partir duquel les utilisateurs finaux effectueront l’installation](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Décrit comment définir l'emplacement à partir duquel les utilisateurs téléchargent et installent l'application.|  
|[Guide pratique pour spécifier le mode d’installation en ligne et hors connexion de ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Décrit comment définir si l'application est disponible hors connexion ou en ligne.|  
|[Guide pratique pour définir la version de publication ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Explique comment définir la ClickOnce **Publish Version** propriété qui détermine si l’application que vous publiez sera traitée comme une mise à jour.|  
|[Guide pratique pour incrémenter automatiquement la version de publication ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Décrit comment incrémenter automatiquement le numéro de révision de le **PublishVersion** chaque fois que vous publiez l’application.|  
  
 Pour plus d’informations, consultez [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Boîte de dialogue Fichiers d'application  
 Cette boîte de dialogue vous permet de spécifier comment les fichiers de votre projet sont classés pour la publication, le téléchargement dynamique et la mise à jour. Elle contient une grille qui répertorie les fichiers projet qui ne sont pas exclus par défaut ou qui ont un groupe de téléchargement.  
  
 Pour exclure des fichiers, marquer les fichiers comme les fichiers de données ou les composants requis et créer des groupes de fichiers pour une installation conditionnelle dans l’interface utilisateur de Visual Studio, consultez [Comment : spécifier lequel fichiers publiés via ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Vous pouvez également marquer des fichiers de données à l'aide de Mage.exe. Pour plus d'informations, consultez [Comment : inclure un fichier de données dans une application ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Composants requis, boîte de dialogue  
 Cette boîte de dialogue spécifie quels composants requis sont installés, ainsi que la manière dont ils sont installés. Pour plus d’informations, consultez [Comment : installer les composants requis avec une Application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) et [boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Boîte de dialogue Mises à jour des applications  
 Cette boîte de dialogue spécifie comment l'installation de l'application doit vérifier les mises à jour. Pour plus d’informations, consultez [Comment : gérer les mises à jour pour une Application ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Boîte de dialogue Options de publication  
 La boîte de dialogue Options de publication spécifie les options de déploiement d'une application.  
  
|||  
|-|-|  
|[Guide pratique pour changer la langue de publication pour une application ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Explique comment spécifier une langue et une culture correspondant à la version localisée.|  
|[Guide pratique pour spécifier un nom de menu Démarrer pour une application ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Décrit comment modifier le nom complet d'une application ClickOnce.|  
|[Guide pratique pour spécifier un lien pour le support technique](../deployment/how-to-specify-a-link-for-technical-support.md)|Explique comment définir la **URL de support technique** propriété, qui identifie une page Web ou un partage de fichiers où les utilisateurs peuvent accéder pour obtenir des informations sur l’application.|  
|[Guide pratique pour spécifier une URL du support technique pour chaque prérequis lors d’un déploiement ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|A montré comment modifier manuellement un manifeste d'application pour inclure les URL de support technique de chaque composant requis.|  
|[Guide pratique pour spécifier une page de publication pour une application ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Décrit comment générer et publier une page web par défaut (publish.htm) en même temps que l’application|  
|[Comment : personnaliser la Page Web par défaut de ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Décrit comment personnaliser la page web qui est automatiquement générée et publiée avec l’application.|  
|[Guide pratique pour activer le démarrage automatique pour les installations depuis un CD-ROM](../deployment/how-to-enable-autostart-for-cd-installations.md)|Décrit comment activer le démarrage automatique afin que l'application ClickOnce soit lancée automatiquement lorsque le média est inséré.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour créer des associations de fichiers pour une application ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Décrit comment ajouter la prise en charge d’extension de nom de fichier à une application ClickOnce.|  
|[Guide pratique pour récupérer les informations de chaîne de requête dans une application ClickOnce en ligne](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Montre comment récupérer des paramètres passés dans l'URL utilisée pour exécuter une application ClickOnce.|  
|[Guide pratique pour suspendre l’activation des URL des applications ClickOnce à l’aide du concepteur](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Décrit comment forcer les utilisateurs à démarrer l’application à partir de la **Démarrer** menu à l’aide du concepteur.|  
|[Guide pratique pour suspendre l’activation des URL des applications ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Décrit comment forcer les utilisateurs à démarrer l’application à partir de la **Démarrer** menu.|  
|[Procédure pas à pas : téléchargement d’assemblys à la demande avec l’API du déploiement ClickOnce à l’aide du concepteur](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Explique comment télécharger les assemblys d'application uniquement lors de leur première utilisation par l'application à l'aide du concepteur.|  
|[Procédure pas à pas : téléchargement d’assemblys à la demande avec l’API de déploiement ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Explique comment télécharger les assemblys d'application uniquement lors de leur première utilisation par l'application.|  
|[Procédure pas à pas : téléchargement d’assemblys satellites à la demande avec l’API de déploiement ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Décrit comment marquer vos assemblys satellites comme facultatifs et télécharger uniquement l'assembly nécessaire à un ordinateur client pour ses paramètres de culture actuels.|  
|[Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Explique comment utiliser les outils du .NET Framework pour déployer votre application ClickOnce.|  
|[Procédure pas à pas : déploiement manuel d’une application ClickOnce qui ne nécessite pas de nouvelle signature et qui conserve les informations relatives à la personnalisation](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)|Explique comment utiliser les outils du .NET Framework pour déployer votre application ClickOnce sans signer à nouveau les manifestes.|  
|[Guide pratique pour configurer des projets pour des plateformes cibles](../ide/how-to-configure-projects-to-target-platforms.md)|Explique comment publier pour un processeur 64 bits en modifiant le **unité centrale cible** ou **plateforme cible** propriété dans votre projet.|  
|[Procédure pas à pas : L’activation d’une Application ClickOnce pour s’exécuter sur plusieurs Versions du .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Explique comment permettre à une application ClickOnce de s'installer et de s'exécuter sur plusieurs versions du .NET Framework.|  
|[Procédure pas à pas : création d’un programme d’installation personnalisé pour une application ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Explique comment créer un programme d'installation personnalisé pour installer une application ClickOnce.|  
|[Guide pratique pour publier une application WPF avec les styles visuels activés](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Fournit les instructions pas à pas pour résoudre une erreur qui s'affiche lorsque vous essayez de publier une application WPF pour laquelle les styles visuels sont activés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Informations de référence sur ClickOnce](../deployment/clickonce-reference.md)