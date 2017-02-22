---
title: "Mod&#232;les de prise en charge des sites Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Nous les projets, les modèles de site"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Mod&#232;les de prise en charge des sites Web
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

les modèles de projet et d'élément de site Web de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournissent des stubs réutilisables et personnalisables de projets et d'éléments de site Web qui accélèrent le processus de développement en supprimant le besoin de créer des projets et des éléments de site web à partir de zéro.  Pour plus d'informations sur les modèles de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , consultez l' [Création de modèles de projets et d'éléments personnalisés](../../ide/creating-project-and-item-templates.md).  
  
## Dossier de modèles de projet  
 Les modèles de modèle de projet Web sont généralement installés sur*chemin d'installation de Visual Studio*\[\] \\Common7\\IDE\\ProjectTemplates\\Web \\, chacun dans un sous\-dossier nommé d'après le langage de programmation web.  
  
## Fichier projet  
 L'environnement de développement intégré \(IDE\) de \(IDE\)  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requiert une extension de fichier projet comme un moyen de mapper un modèle en type correct de projet.  Comme les projets Web n'ont pas un fichier projet, l'extension de fichier projet fictif .webproj est inscrite pour prendre en charge ce comportement.  
  
 Éventuellement, une chaîne de nom de langue peut être ajoutée au modèle pour permettre au système de projet Web pour définir la valeur par défaut de langage dans la boîte de dialogue d' **Ajouter un nouvel élément** pour les éléments selon le modèle.  La chaîne doit être la première ligne du fichier et doit correspondre à celui stocké sous AddItemLanguageName dans l'inscription du moteur Intellisense et le nom enregistré sous le sous\-type de projet \(VsTemplate\).  Pour plus d'informations, consultez [Attributs de prise en charge de Site Web](../../extensibility/internals/web-site-support-attributes.md).  
  
 Si la chaîne n'est pas présente, le système de projet Web tente de déterminer la langue par défaut basée sur l'attribut de langage et les extensions de fichier des pages ajoutées au projet Web par le modèle de projet.  
  
## Modèles de projet  
 Les modèles de projet de site Web sont utilisés pour générer des sites web en réponse à la commande de **Nouveau site Web** dans le menu de **Fichier** .  trois types de projet de site Web sont actuellement pris en charge :  
  
-   projets vides de site Web  
  
-   Projets de site Web  
  
-   projets de service Web  
  
### projets vides de site Web  
 Ces fichiers créent un site Web vide en réponse à la commande de **site Web vide** , qui est disponible après avoir pointe vers **Nouveau site Web** dans le menu de **Fichier** :  
  
-   EmptyWeb.vstemplate  
  
     Le fichier modèle qui guident la création du nouveau site Web vide.  
  
-   EmptyWeb.webproj  
  
     ce fichier est un artefact du système de modèle de projet.  il satisfait la référence de fichier projet dans le fichier d'EmptyWeb.vstemplate.  
  
### projets de site Web  
 Ces fichiers créent un site web en réponse à la commande de **Site Web ASP.NET** , qui est disponible après avoir pointe vers **Nouveau site Web** dans le menu de **Fichier** :  
  
-   Default.aspx  
  
     La page d'accueil par défaut pour le site web.  L'attribut de langage spécifie le langage codebehind, et l'attribut CodeFile spécifie le fichier dépendant contenant le code codebehind associé à cette page.  
  
-   Default.aspx.*extension*  
  
     Le fichier dépendant qui contient le code codebehind pour la page d'accueil par défaut.  Le langage codebehind détermine *extension* de ce fichier.  
  
-   web.config  
  
     le fichier de configuration de la racine web.site.  
  
-   WebApplication.vstemplate  
  
     Le fichier modèle qui détermine le contenu de la solution de site Web et force la création du dossier App\_Data.  
  
-   WebApplication.webproj  
  
     ce fichier est un artefact du système de modèle de projet.  il satisfait la référence de fichier projet dans le fichier de WebApplication.vstemplate.  
  
### projets de service Web  
 Ces fichiers créent un site web en réponse à la commande de **Service Web ASP.NET** qui est disponible après avoir pointe vers **Nouveau site Web** dans le menu de **Fichier** :  
  
-   Service.asmx  
  
     La page HTML pour le service Web.  L'attribut de langage spécifie le langage codebehind, et l'attribut CodeBehind spécifie le fichier dépendant contenant le code codebehind associé à ce service.  
  
-   service. *extension*  
  
     le fichier dépendant qui implémente la classe de service.  Le langage codebehind détermine *extension* de ce fichier.  
  
-   web.config  
  
-   le fichier de configuration de la racine web.site.  
  
-   WebService.vstemplate  
  
     Le fichier modèle qui détermine le contenu de la solution de site Web et force la création de dossiers App\_Data et App\_Code.  le service. le fichier d'extension est copié dans le dossier App\_Code.  
  
-   WebService.webproj  
  
     ce fichier est un artefact du système de modèle de projet.  il satisfait la référence de fichier projet dans le fichier de WebService.vstemplate.  
  
## Dossier de modèles d'élément de projet  
 Les modèles de modèle d'élément de projet de site Web sont généralement installés sur*chemin d'installation de Visual Studio*\[\] \\Common7\\IDE\\ItemTemplates\\Web \\, chacun dans un sous\-dossier nommé d'après son langage de programmation web.  
  
## Modèles d'élément de projet  
 Les modèles d'élément de projet de site Web sont utilisés pour ajouter de nouvelles pages Web sur un site Web en réponse à la commande d' **Ajouter un élément existant** .  Ces types de pages Web sont actuellement pris en charge :  
  
-   nouvelle classe  
  
-   nouvelle page HTML  
  
-   nouveau formulaire web  
  
-   nouvelle page maître  
  
### nouvelle classe  
 Ce modèle crée un fichier source qui définit une classe vide en réponse à la commande d' **ajoutez la nouvelle classe** .  
  
-   classe. *extension*  
  
     le fichier source qui implémente la classe vide.  Le langage codebehind détermine *extension* de ce fichier.  
  
-   Class.vstemplate  
  
     le fichier modèle qui crée le fichier source et détermine son contenu.  
  
### nouvelle page HTML  
 Ce modèle crée une page Web en réponse à la commande d' **ajoutez la nouvelle page HTML** .  
  
-   HTMLPage.htm  
  
     Le contenu à partir de la page Web.  Cette page Web est généralement sans fichier associé du dépendant codebehind.  Pour créer une page intelligente avec un fichier associé codebehind, utilisez le modèle de formulaire web à la place.  
  
-   HTMLPage.vstemplate  
  
     le fichier modèle qui crée la page Web et détermine son contenu.  
  
### nouveau WebForm  
 Ce modèle crée une page Web intelligente en réponse à la commande d' **ajoutez le nouveau formulaire web** .  
  
 Pour créer un fichier source dépendant codebehind, sélectionnez **Placer le code dans un fichier distinct**.  Sinon une page Web unique qui a un bloc vide de script et aucune directive de la page %\> d'\<% de raccorder un fichier dépendant.  
  
 pour créer une page de contenu pour une page maître sélectionnée, sélectionnez **Sélectionner la page maître**.  
  
-   WebForm.aspx  
  
     Le contenu à partir de la page Web.  Cette page Web n'a aucun fichier associé du dépendant codebehind.  
  
-   WebForm\_cb.aspx  
  
     Le contenu à partir de la page Web.  Cette page Web est associée à un fichier dépendant codebehind.  
  
-   Codebehind. *extension*  
  
     le fichier dépendant qui implémente la classe de webform.  Le langage codebehind détermine *extension* de ce fichier.  
  
-   ContentPage.aspx  
  
     Le contenu à partir de la page Web comme une page de contenu.  Cette page Web n'a aucun fichier associé du dépendant codebehind.  
  
-   ContentPage\_cb.aspx  
  
     Le contenu à partir de la page Web comme une page de contenu.  Cette page Web est associée à un fichier dépendant codebehind.  
  
-   WebForm.vstemplate  
  
     Le fichier modèle qui détermine le contenu de la nouvelle page Web et de son fichier dépendant le cas échéant.  
  
### nouvelle page maître  
 Ce modèle crée une page maître en réponse à la commande d' **ajoutez la nouvelle page maître** .  
  
 Pour créer un fichier source dépendant codebehind, sélectionnez **Placer le code dans un fichier distinct**.  Sinon une page Web unique qui a un bloc vide de script et aucune directive de la page %\> d'\<% de raccorder un fichier dépendant.  
  
-   MasterPage.master  
  
     Le contenu à partir de la page maître.  Cette page maître n'a aucun fichier associé du dépendant codebehind.  
  
-   MasterPage\_cb.master  
  
     Le contenu à partir de la page maître.  Cette page maître a associée à un fichier dépendant codebehind.  
  
-   Codebehind.*extension*  
  
     le fichier dépendant qui implémente la classe de page maître.  Le langage codebehind détermine *extension* de ce fichier.  
  
-   MasterPage.vstemplate  
  
     Le fichier modèle qui détermine le contenu de la page maître et de son fichier dépendant le cas échéant.  
  
## Voir aussi  
 [Prise en charge du Site Web](../../extensibility/internals/web-site-support.md)