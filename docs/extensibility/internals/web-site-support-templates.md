---
title: Modèles de support du site Web Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703450"
---
# <a name="web-site-support-templates"></a>Modèles de prise en charge de site web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Les modèles de projets et d’objets du site Web fournissent des projets et des talons d’éléments réutilisables et personnalisables qui accélèrent le processus de développement en supprimant la nécessité de créer de nouveaux projets et éléments de site Web à partir de zéro. Pour plus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] d’informations sur les modèles, voir [Créer des modèles de projets et d’objets](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Dossier de modèle de projet
 Les modèles de projets Web sont généralement installés sur *[Visual Studio Installation*Path\\] 'Common7'IDE’ProjectTemplates-Web , chacun dans un sous-pliage qui porte le nom du langage de programmation Web.

## <a name="project-file"></a>Fichier projet
 L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) nécessite une extension de fichier de projet comme moyen de cartographier un modèle au bon type de projet. Étant donné que les projets Web n’ont pas de fichier de projet, l’extension de fichier factice du projet .webproj est enregistrée pour cartographier le modèle au type de projet.

 Optionnellement, une chaîne de nom de langue peut être ajoutée au modèle, pour permettre au système de projet Web de définir la valeur par défaut de langage dans la boîte de dialogue **Add New Item** pour les éléments basés sur le modèle. La chaîne doit être la première ligne du fichier. Il doit correspondre à la fois au nom enregistré sous AddItemLanguageName dans l’enregistrement du moteur IntelliSense, et au nom enregistré sous le projet Subtype (VsTemplate). Pour plus d’informations, voir [Attributs de support du site Web](../../extensibility/internals/web-site-support-attributes.md).

 Si la chaîne n’est pas présente, le système de projet Web tente de déterminer le langage par défaut en fonction de l’attribut linguistique et des extensions de fichiers des pages ajoutées au projet Web par le modèle de projet.

## <a name="project-templates"></a>Modèles de projet
 Les modèles de projets de site Web sont utilisés pour construire de nouveaux sites Web en réponse à la commande **du nouveau site Web** sur le menu du **fichier.** Trois types de projets de sites Web sont actuellement pris en charge :

- Projets de sites Web vides

- Projets de sites Web

- Projets de service Web

### <a name="empty-web-site-projects"></a>Projets de sites Web vides
 Ces fichiers créent un nouveau site Web vide en réponse à la commande **de site Web vide,** qui est disponible après avoir choisi **File** > **New Web Site**:

- EmptyWeb.vstemplate

     Le fichier modèle qui guide la création du nouveau site Web vide.

- EmptyWeb.webproj (en)

     Ce fichier est un artefact du système de modèle de projet. Il satisfait la référence de fichier de projet dans le fichier EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Projets de sites Web
 Ces fichiers créent un nouveau site Web en réponse à la commande **ASP.NET site Web,** qui est disponible après avoir choisi **File** > **New Web Site**:

- Default.aspx

     La page d’accueil par défaut pour le nouveau site Web. L’attribut de langue spécifie la langue de codebehind, et l’attribut CodeFile spécifie le fichier dépendant qui contient le code de codebehind associé à cette page.

- Par défaut.aspx. *extension*

     Le fichier à charge qui contient le code de codebehind pour la page d’accueil par défaut. Le langage codebehind détermine *l’extension* de ce fichier.

- web.config

     Le fichier de configuration web.site racine.

- WebApplication.vstemplate (en)

     Le fichier modèle qui détermine le contenu de la solution du site Web et force la création du dossier App_Data.

- WebApplication.webproj (en)

     Ce fichier est un artefact du système de modèle de projet. Il satisfait la référence de fichier de projet dans le fichier WebApplication.vstemplate.

### <a name="web-service-projects"></a>Projets de services Web
 Ces fichiers créent un nouveau site Web en réponse à la commande **ASP.NET service Web,** qui est disponible après avoir choisi **File** > **New Web Site**:

- Service.asmx

     La page HTML du nouveau service Web. L’attribut de langue spécifie la langue de codebehind, et l’attribut CodeBehind spécifie le fichier dépendant qui contient le code de codebehind associé à ce service.

- Service. *Extension*

     Le fichier à charge qui implémente la classe de service. Le langage codebehind détermine *l’extension* de ce fichier.

- web.config

- Le fichier de configuration web.site racine.

- WebService.vstemplate

     Le fichier modèle qui détermine le contenu de la solution du site Web et force la création des dossiers App_Data et App_Code. Le service. le fichier *d’extension* est copié sur le dossier App_Code.

- WebService.webproj (en)

     Ce fichier est un artefact du système de modèle de projet. Il satisfait la référence de fichier de projet dans le fichier WebService.vstemplate.

## <a name="project-item-template-folder"></a>Dossier de modèle d’élément de projet
 Les modèles d’éléments de projet Web sont généralement installés dans [ Visual Studio Installation\\*Path*]

## <a name="project-item-templates"></a>Modèles d’objets de projet
 Les modèles d’éléments de projet de site Web sont utilisés pour ajouter de nouvelles pages Web à un site Web en réponse à la commande **Add Existing Item.** Ces types de pages Web sont actuellement pris en charge :

- Nouvelle classe

- Nouvelle page HTML

- Nouveau formulaire Web

- Nouvelle page maîtresse

### <a name="new-class"></a>Nouvelle classe
 Ce modèle crée un nouveau fichier source qui définit une classe vide en réponse à la commande **Add New Class.**

- Classe *Extension*

     Le fichier source qui implémente la classe vide. Le langage codebehind détermine *l’extension* de ce fichier.

- Classe.vstemplate

     Le fichier modèle qui crée le fichier source et détermine son contenu.

### <a name="new-html-page"></a>Nouvelle page HTML
 Ce modèle crée une nouvelle page Web en réponse à la commande **Add New HTML Page.**

- HTMLPage.htm (en)

     Le contenu de départ de la page Web. Cette page Web n’a généralement pas de fichier dépendant de codebehind associé. Pour créer une page intelligente avec un fichier codébehind associé, utilisez plutôt le modèle web.

- HTMLPage.vstemplate

     Le fichier modèle qui crée la page Web et détermine son contenu.

### <a name="new-webform"></a>Nouveau WebForm
 Ce modèle crée une nouvelle page Web intelligente en réponse à la commande **Add New Web Form.**

 Pour créer un fichier source codebehind dépendant, sélectionnez **le code Place dans un fichier séparé**. Sinon, une seule page Web est créée qui \<a un bloc de script vide et pas de % Page % > directives pour brancher un fichier dépendant.

 Pour créer une page de contenu pour une page maîtresse sélectionnée, **sélectionnez Sélectionnez page principale**Select .

- WebForm.aspx (en)

     Le contenu de départ de la page Web. Cette page Web n’a pas de fichier dépendant de codebehind associé.

- WebForm_cb.aspx

     Le contenu de départ de la page Web. Cette page Web dispose d’un fichier dépendant de codebehind associé.

- Codebehind. *Extension*

     Le fichier à charge qui implémente la classe webform. Le langage codebehind détermine *l’extension* de ce fichier.

- ContentPage.aspx (en)

     Le contenu de départ de la page Web sous forme de page de contenu. Cette page Web n’a pas de fichier dépendant de codebehind associé.

- ContentPage_cb.aspx

     Le contenu de départ de la page Web sous forme de page de contenu. Cette page Web dispose d’un fichier dépendant de codebehind associé.

- WebForm.vstemplate

     Le fichier modèle qui détermine le contenu de la nouvelle page Web et de son fichier à charge, le cas échéant.

### <a name="new-master-page"></a>Nouvelle page Master
 Ce modèle crée une nouvelle page principale en réponse à la commande **Add New Master Page.**

 Pour créer un fichier source codebehind dépendant, sélectionnez **le code Place dans un fichier séparé**. Sinon, une seule page Web est créée qui \<a un bloc de script vide et pas de % Page % > directives pour brancher un fichier dépendant.

- MasterPage.master (en)

     Le contenu de départ de la page principale. Cette page principale n’a pas de fichier dépendant de codebehind associé.

- MasterPage_cb.master

     Le contenu de départ de la page principale. Cette page principale dispose d’un fichier dépendant de codebehind associé.

- Codebehind. *extension*

     Le fichier à charge qui implémente la classe de page principale. Le langage codebehind détermine *l’extension* de ce fichier.

- MasterPage.vstemplate

     Le fichier modèle qui détermine le contenu de la nouvelle page principale et de son fichier à charge, le cas échéant.

## <a name="see-also"></a>Voir aussi
- [Prise en charge de site web](../../extensibility/internals/web-site-support.md)
