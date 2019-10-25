---
title: Modèles de prise en charge de site Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aceaa574fa2a0148236f033c610f8c53ca74e635
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721599"
---
# <a name="web-site-support-templates"></a>Modèles de prise en charge de site web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modèles de projet et d’élément de site Web fournissent un projet de site Web réutilisable et personnalisable et des stubs d’élément qui accélèrent le processus de développement en éliminant le besoin de créer de nouveaux projets et éléments de site Web à partir de zéro. Pour plus d’informations sur les modèles de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], consultez [création de modèles de projet et d’élément](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Dossier de modèles de projet
 Les modèles de projet Web sont généralement installés sur [*chemin d’installation de Visual Studio*] \Common7\IDE\ProjectTemplates\Web \\, chacun dans un sous-dossier nommé d’après le langage de programmation Web.

## <a name="project-file"></a>Fichier projet
 L’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nécessite une extension de fichier projet pour mapper un modèle au type de projet approprié. Étant donné que les projets Web n’ont pas de fichier projet, l’extension de fichier projet factice. webproj est inscrite pour mapper le modèle au type de projet.

 Éventuellement, une chaîne de nom de langue peut être ajoutée au modèle, pour permettre au système de projet Web de définir la langue par défaut dans la boîte de dialogue **Ajouter un nouvel élément** pour les éléments basés sur le modèle. La chaîne doit être la première ligne du fichier. Il doit correspondre à la fois au nom enregistré sous AddItemLanguageName dans l’inscription du moteur IntelliSense et au nom enregistré sous le sous-type de projet (VsTemplate). Pour plus d’informations, consultez [attributs de prise en charge de site Web](../../extensibility/internals/web-site-support-attributes.md).

 Si la chaîne n’est pas présente, le système de projet Web tente de déterminer la langue par défaut en fonction de l’attribut de langue et des extensions de fichier des pages ajoutées au projet Web par le modèle de projet.

## <a name="project-templates"></a>Modèles de projet
 Les modèles de projet de site Web sont utilisés pour générer de nouveaux sites Web en réponse à la commande **nouveau site Web** dans le menu **fichier** . Trois types de projets de site Web sont actuellement pris en charge :

- Projets de site Web vides

- Projets de site Web

- Projets de service Web

### <a name="empty-web-site-projects"></a>Projets de site Web vides
 Ces fichiers créent un nouveau site Web vide en réponse à la commande de **site Web vide** , qui est disponible après avoir choisi **fichier**  > **nouveau site Web**:

- EmptyWeb. vstemplate

     Fichier de modèle qui guide la création du nouveau site Web vide.

- EmptyWeb. webproj

     Ce fichier est un artefact du système de modèles de projet. Elle répond à la référence de fichier projet dans le fichier EmptyWeb. vstemplate.

### <a name="web-site-projects"></a>Projets de site Web
 Ces fichiers créent un nouveau site Web en réponse à la commande de **site web ASP.net** , disponible après avoir choisi le **fichier**  > **nouveau site Web**:

- Default.aspx

     Page d’hébergement par défaut pour le nouveau site Web. L’attribut Language spécifie le langage codebehind, et l’attribut CodeFile spécifie le fichier dépendant qui contient le code codebehind associé à cette page.

- Default. aspx. *extension*

     Fichier dépendant qui contient le code codebehind de la page d’hébergement par défaut. Le langage codebehind détermine l' *extension* de ce fichier.

- web.config

     Fichier de configuration Web. site racine.

- WebApplication. vstemplate

     Fichier de modèle qui détermine le contenu de la solution de site Web et force la création du dossier App_Data.

- WebApplication. webproj

     Ce fichier est un artefact du système de modèles de projet. Elle répond à la référence de fichier projet dans le fichier WebApplication. vstemplate.

### <a name="web-service-projects"></a>Projets de service Web
 Ces fichiers créent un nouveau site Web en réponse à la commande du **service web ASP.net** , disponible après avoir choisi le **fichier**  > **nouveau site Web**:

- Service. asmx

     Page HTML pour le nouveau service Web. L’attribut Language spécifie le langage codebehind, et l’attribut CodeBehind spécifie le fichier dépendant qui contient le code codebehind associé à ce service.

- Services. *poste*

     Fichier dépendant qui implémente la classe de service. Le langage codebehind détermine l' *extension* de ce fichier.

- web.config

- Fichier de configuration Web. site racine.

- Service Web. vstemplate

     Fichier de modèle qui détermine le contenu de la solution de site Web et force la création des dossiers App_Data et App_Code. Service. le fichier d' *extension* est copié dans le dossier App_Code.

- Service Web. webproj

     Ce fichier est un artefact du système de modèles de projet. Elle répond à la référence de fichier projet dans le fichier WebService. vstemplate.

## <a name="project-item-template-folder"></a>Dossier du modèle d’élément de projet
 Les modèles d’élément de projet Web sont généralement installés dans [*chemin d’installation de Visual Studio*] \Common7\IDE\ItemTemplates\Web \\, chacun dans un sous-dossier nommé d’après le langage de programmation Web.

## <a name="project-item-templates"></a>Modèles d’élément de projet
 Les modèles d’élément de projet de site Web sont utilisés pour ajouter de nouvelles pages Web à un site Web en réponse à la commande **Ajouter un élément existant** . Ces types de pages Web sont actuellement pris en charge :

- Nouvelle classe

- Nouvelle page HTML

- Nouveau formulaire Web

- Nouvelle page maître

### <a name="new-class"></a>Nouvelle classe
 Ce modèle crée un nouveau fichier source qui définit une classe vide en réponse à la commande **Ajouter une nouvelle classe** .

- Classe *poste*

     Fichier source qui implémente la classe vide. Le langage codebehind détermine l' *extension* de ce fichier.

- Class. vstemplate

     Fichier de modèle qui crée le fichier source et détermine son contenu.

### <a name="new-html-page"></a>Nouvelle page HTML
 Ce modèle crée une nouvelle page Web en réponse à la commande **Ajouter une nouvelle page HTML** .

- HTMLPage. htm

     Contenu de départ de la page Web. En général, cette page Web n’a aucun fichier dépendant du codebehind associé. Pour créer une page intelligente avec un fichier codebehind associé, utilisez le modèle de formulaire Web à la place.

- HTMLPage. vstemplate

     Fichier de modèle qui crée la page Web et détermine son contenu.

### <a name="new-webform"></a>Nouveau WebForm
 Ce modèle crée une page Web active en réponse à la commande **Ajouter un nouveau formulaire Web** .

 Pour créer un fichier source codebehind dépendant, sélectionnez **Placer le code dans un fichier distinct**. Dans le cas contraire, une seule page Web est créée avec un bloc de script vide et aucune directive \<% page% > pour raccorder un fichier dépendant.

 Pour créer une page de contenu pour une page maître sélectionnée, sélectionnez **Sélectionner une page maître**.

- WebForm. aspx

     Contenu de départ de la page Web. Cette page Web n’a aucun fichier dépendant du codebehind associé.

- WebForm_cb. aspx

     Contenu de départ de la page Web. Cette page Web est associée à un fichier dépendant du codebehind.

- Behind. *poste*

     Fichier dépendant qui implémente la classe WebForm. Le langage codebehind détermine l' *extension* de ce fichier.

- ContentPage. aspx

     Contenu de départ de la page Web sous forme de page de contenu. Cette page Web n’a aucun fichier dépendant du codebehind associé.

- ContentPage_cb. aspx

     Contenu de départ de la page Web sous forme de page de contenu. Cette page Web est associée à un fichier dépendant du codebehind.

- WebForm. vstemplate

     Fichier de modèle qui détermine le contenu de la nouvelle page Web et de son fichier dépendant, le cas échéant.

### <a name="new-master-page"></a>Nouvelle page maître
 Ce modèle crée une nouvelle page maître en réponse à la commande **Ajouter une nouvelle page maître** .

 Pour créer un fichier source codebehind dépendant, sélectionnez **Placer le code dans un fichier distinct**. Dans le cas contraire, une seule page Web est créée avec un bloc de script vide et aucune directive \<% page% > pour raccorder un fichier dépendant.

- MasterPage. Master

     Contenu de départ de la page maître. Cette page maître n’a aucun fichier dépendant du codebehind associé.

- MasterPage_cb. Master

     Contenu de départ de la page maître. Cette page maître est associée à un fichier dépendant du codebehind.

- Behind. *extension*

     Fichier dépendant qui implémente la classe de page maître. Le langage codebehind détermine l' *extension* de ce fichier.

- MasterPage. vstemplate

     Fichier de modèle qui détermine le contenu de la nouvelle page maître et de son fichier dépendant, le cas échéant.

## <a name="see-also"></a>Voir aussi
- [Prise en charge de site Web](../../extensibility/internals/web-site-support.md)