---
title: "Modèles de prise en charge du Site Web | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b17674b8cd5058ec20db4c483b2c3508aa275b29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support-templates"></a>Modèles de prise en charge des sites Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Modèles de projet et d’élément de site Web fournissent un site Web réutilisables et personnalisables des stubs qui accélèrent le processus de développement en supprimant la nécessité de créer de nouveaux projets de site Web et des éléments à partir de zéro. Pour plus d’informations sur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèles, consultez [création de modèles de projet et élément](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Dossier de modèle de projet  
 Modèles de modèle de projet Web sont généralement installés sur [*le chemin d’accès de Visual Studio Installation*] \Common7\IDE\ProjectTemplates\Web\\, chacune d’elles dans un sous-dossier nommé d’après le langage de programmation de web.  
  
## <a name="project-file"></a>Fichier projet  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) requiert une extension de fichier projet comme permet de mapper un modèle pour le type de projet approprié. Étant donné que les projets Web n’ont pas un fichier projet, le .webproj d’extension de fichier projet factice est inscrit pour cette prise en charge.  
  
 Si vous le souhaitez, une chaîne de nom de langue peut être ajoutée au modèle pour activer le système de projet Web définir la langue par défaut dans le **ajouter un nouvel élément** boîte de dialogue pour les éléments basés sur le modèle. La chaîne doit être la première ligne du fichier et doit correspondre au nom enregistré sous AddItemLanguageName dans l’inscription du moteur Intellisense et le nom inscrit sous le projet Subtype(VsTemplate). Pour plus d’informations, consultez [Site Web de prise en charge des attributs](../../extensibility/internals/web-site-support-attributes.md).  
  
 Si la chaîne n’est pas présente, le système de projet Web va tenter de déterminer la langue par défaut basée sur les extensions de langage fichier des attributs et des pages ajoutés au projet Web par le modèle de projet.  
  
## <a name="project-templates"></a>Modèles de projet  
 Modèles de projet de site Web sont utilisés pour générer de nouveaux sites Web en réponse à la **nouveau Site Web** commande sur le **fichier** menu. Trois types de projets de site Web sont actuellement prises en charge :  
  
-   Projets de site Web vide  
  
-   Projets de site Web  
  
-   Projets de service Web  
  
### <a name="empty-web-site-projects"></a>Projets de Site Web vide  
 Ces fichiers de créent un nouveau site Web vide en réponse à la **Site Web vide** commande, qui est disponible après pointant vers **nouveau Site Web** sur la **fichier** menu :  
  
-   EmptyWeb.vstemplate  
  
     Le fichier de modèle qui guide la création du nouveau site Web vide.  
  
-   EmptyWeb.webproj  
  
     Ce fichier est un artefact du système de modèle de projet. Il répond à la référence de fichier de projet dans le fichier EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Projets de Site Web  
 Ces fichiers de créent un nouveau site Web en réponse à la **Site Web ASP.NET** commande, qui est disponible après pointant vers **nouveau Site Web** sur la **fichier** menu :  
  
-   Default.aspx  
  
     La page d’accueil par défaut pour le nouveau site Web. L’attribut de langage spécifie le langage de code-behind et l’attribut CodeFile Spécifie le fichier dépendant qui contient le code de code-behind associé à cette page.  
  
-   Default.aspx. *extension*  
  
     Le fichier dépendant qui contient le code du code-behind pour la page d’accueil par défaut. Le langage de code-behind détermine le *extension* de ce fichier.  
  
-   web.config  
  
     Le fichier de configuration web.site racine.  
  
-   WebApplication.vstemplate  
  
     Le fichier de modèle qui détermine le contenu de la solution de site Web et force la création du dossier App_Data.  
  
-   WebApplication.webproj  
  
     Ce fichier est un artefact du système de modèle de projet. Il répond à la référence de fichier de projet dans le fichier WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Projets de Service Web  
 Ces fichiers de créent un nouveau site Web en réponse à la **Service Web ASP.NET** commande disponible après pointant vers **nouveau Site Web** sur la **fichier** menu :  
  
-   Service.asmx  
  
     La page HTML pour le nouveau service Web. L’attribut de langage spécifie le langage de code-behind et l’attribut code-behind Spécifie le fichier dépendant contenant le code de code-behind associé à ce service.  
  
-   Service. *extension*  
  
     Le fichier dépendant qui implémente la classe de service. Le langage de code-behind détermine le *extension* de ce fichier.  
  
-   web.config  
  
-   Le fichier de configuration web.site racine.  
  
-   WebService.vstemplate  
  
     Le fichier de modèle qui détermine le contenu de la solution de site Web et force la création des dossiers App_Data et App_Code. Le service. *extension* fichier est copié dans le dossier App_Code.  
  
-   WebService.webproj  
  
     Ce fichier est un artefact du système de modèle de projet. Il répond à la référence de fichier de projet dans le fichier WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Dossier de modèles d’élément de projet  
 Modèles de modèle d’élément de projet Web sont généralement installés sur [*le chemin d’accès de Visual Studio Installation*] \Common7\IDE\ItemTemplates\Web\\, chacune d’elles dans un sous-dossier nommé d’après son langage de programmation pour le web.  
  
## <a name="project-item-templates"></a>Modèles d’élément de projet  
 Modèles d’élément de projet de site Web sont utilisés pour ajouter de nouvelles pages Web sur un site Web en réponse à la **ajouter un élément existant** commande. Ces types de pages Web sont actuellement pris en charge :  
  
-   Nouvelle classe  
  
-   Nouvelle page HTML  
  
-   Nouveau formulaire Web  
  
-   Nouvelle page maître  
  
### <a name="new-class"></a>Nouvelle classe  
 Ce modèle crée un fichier source qui définit une classe vide en réponse à la **ajouter une nouvelle classe** commande.  
  
-   Classe *extension*  
  
     Le fichier source qui implémente la classe vide. Le langage de code-behind détermine le *extension* de ce fichier.  
  
-   Class.vstemplate  
  
     Le fichier de modèle qui crée le fichier source et détermine son contenu.  
  
### <a name="new-html-page"></a>Nouvelle Page HTML  
 Ce modèle crée une nouvelle page Web en réponse à la **ajouter une nouvelle Page HTML** commande.  
  
-   HTMLPage.htm  
  
     Le contenu de départ de la page Web. Cette page Web n’a généralement aucun fichier dépendant du code-behind associé. Pour créer une page active avec un fichier code-behind associés, utilisez le modèle de formulaire Web à la place.  
  
-   HTMLPage.vstemplate  
  
     Le fichier de modèle qui crée la page Web et détermine son contenu.  
  
### <a name="new-webform"></a>Formulaire Web  
 Ce modèle crée une nouvelle page Web active en réponse à la **ajouter un nouveau formulaire Web** commande.  
  
 Pour créer un fichier de source de code-behind dépendants, sélectionnez **placer le code dans un fichier distinct**. Sinon, une page Web unique est créée qui a un bloc de script vide et aucun \<Page % > directives pour raccorder un fichier dépendant.  
  
 Pour créer une page de contenu pour une page maître sélectionnée, sélectionnez **sélectionnez page maître**.  
  
-   WebForm.aspx  
  
     Le contenu de départ de la page Web. Cette page Web n’a aucun fichier dépendant du code-behind associé.  
  
-   WebForm_cb.aspx  
  
     Le contenu de départ de la page Web. Cette page Web a un fichier dépendant du code-behind associé.  
  
-   Code-behind. *extension*  
  
     Le fichier dépendant qui implémente la classe de formulaire Web. Le langage de code-behind détermine le *extension* de ce fichier.  
  
-   ContentPage.aspx  
  
     Le contenu de départ de la page Web comme une page de contenu. Cette page Web n’a aucun fichier dépendant du code-behind associé.  
  
-   ContentPage_cb.aspx  
  
     Le contenu de départ de la page Web comme une page de contenu. Cette page Web a un fichier dépendant du code-behind associé.  
  
-   WebForm.vstemplate  
  
     Le fichier de modèle qui détermine le contenu de la nouvelle page web et ses fichiers dépendants, le cas échéant.  
  
### <a name="new-master-page"></a>Nouvelle Page maître  
 Ce modèle crée une nouvelle page maître en réponse à la **ajouter une nouvelle Page maître** commande.  
  
 Pour créer un fichier de source de code-behind dépendants, sélectionnez **placer le code dans un fichier distinct**. Sinon, une page Web unique est créée qui a un bloc de script vide et aucun \<Page % > directives pour raccorder un fichier dépendant.  
  
-   MasterPage.master  
  
     Le contenu de départ de la page maître. Cette page maître n’a aucun fichier dépendant du code-behind associé.  
  
-   MasterPage_cb.master  
  
     Le contenu de départ de la page maître. Cette page maître est un fichier dépendant du code-behind associé.  
  
-   Code-behind. *extension*  
  
     Le fichier dépendant qui implémente la classe de page maître. Le langage de code-behind détermine le *extension* de ce fichier.  
  
-   MasterPage.vstemplate  
  
     Le fichier de modèle qui détermine le contenu de la nouvelle page maître et ses fichiers dépendants, le cas échéant.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de site Web](../../extensibility/internals/web-site-support.md)