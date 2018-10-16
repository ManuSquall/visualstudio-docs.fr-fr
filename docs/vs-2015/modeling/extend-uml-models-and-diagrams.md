---
title: Étendre les modèles et diagrammes UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0fa0196000e2349f5f323d28138186b59ae07cfd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179125"
---
# <a name="extend-uml-models-and-diagrams"></a>Étendre des diagrammes et des modèles UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique résume les différentes manière d’étendre les outils de modélisation UML fournis avec Visual Studio. Pour connaître les versions de Visual Studio qui prennent en charge chaque outil et type de modèle, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Dans l’exemple de scénario suivant, Fabrikam conçoit et installe des systèmes de gestion de bagages pour les aéroports. D’un projet d’aéroport à un autre, il existe de nombreuses similitudes en termes d’équipement de base et de logiciel de contrôle. Toutefois, plusieurs facteurs peuvent également varier considérablement, comme la configuration des tapis roulants, des bureaux d’enregistrement, des emplacements de stockage et d’autres équipements de manutention de bagages.  
  
 Au démarrage d’un nouveau projet, l’équipe Fabrikam crée un modèle UML pour faciliter la discussion de ces impératifs, à la fois au sein de l’équipe et avec le client. Elle utilise des diagrammes d’activités pour représenter le flux des bagages, avec des nœuds d’objets qui représentent chaque élément d’équipement. Le modèle UML ne représente pas directement le code du système.  
  
 L’équipe Fabrikam responsable des outils effectue une série d’améliorations pour aider les équipes de développement. Les sections suivantes décrivent les différents genres d’extensions que vous pouvez définir. Vous pouvez combiner plusieurs de ces techniques dans une même extension Visual Studio.  
  
 Pour plus d’informations, consultez cette vidéo : ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo")[série MSDN Comment faire : outils UML et extensibilité](http://go.microsoft.com/fwlink/?LinkId=214467).  
  
##  <a name="Requirements"></a> Spécifications  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
-   [Kit de développement logiciel (SDK) de modélisation pour Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).  
  
## <a name="profiles"></a>Profils  
 Les profils permettent de définir des stéréotypes et des propriétés supplémentaires sur des éléments UML.  
  
 Les développeurs d’outils de Fabrikam définissent des stéréotypes sur les nœuds d’objets des diagrammes d’activités, tels que « tapis roulant » et « bureau d’enregistrement ». Quand un membre de l’équipe crée un schéma de manutention de bagages à l’aide d’un diagramme d’activités, les développeurs peuvent désormais définir des stéréotypes pour indiquer le type d’équipement que chaque nœud représente. Les développeurs d’outils définissent des propriétés supplémentaires sur certains des stéréotypes, pour que les utilisateurs puissent enregistrer des valeurs telles que la capacité d’un tapis roulant et l’ergonomie d’un bureau d’enregistrement.  
  
 Pour plus d’informations, consultez [définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md).  
  
## <a name="custom-toolbox-items"></a>Éléments de la boîte à outils personnalisés  
 Un élément de boîte à outils personnalisé crée un élément ou un groupe d’éléments à partir d’un prototype que vous définissez dans un diagramme. Vous pouvez par exemple créer un outil qui crée des cas d’usage dans une couleur ou un stéréotype particulier, ou un groupe de classes et d’associations qui représente un modèle de conception. Vous pouvez ajouter ces éléments de boîte à outils aux extensions Visual Studio et les distribuer à d’autres utilisateurs.  
  
 Pour plus d’informations, consultez [définir un personnalisé élément de boîte à outils de modélisation](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
## <a name="validation"></a>Validation  
 Vous pouvez définir des règles pour vous assurer qu’un modèle UML est conforme aux contraintes spécifiées.  
  
 Les développeurs d’outils de Fabrikam définissent des règles pour aider les membres de l’équipe à éviter les erreurs élémentaires dans les modèles de manutention de bagages. Par exemple, un bureau d’enregistrement ne peut pas être connecté directement à un emplacement de stockage. Il doit y avoir au moins un tapis roulant entre eux.  
  
 Pour plus d’informations, consultez [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="menu-commands"></a>Commandes de menu  
 Vous pouvez définir des commandes que les utilisateurs peuvent appeler en cliquant avec le bouton droit sur les éléments d’un diagramme UML. Les commandes peuvent mettre à jour le modèle et les diagrammes ou exécuter d'autres opérations dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
 Fabrikam définit des commandes de menu qui automatisent des opérations courantes, telles que la création d’un bureau d’enregistrement et sa connexion à un tapis roulant sélectionné ou la réorganisation d’un diagramme en fonction des règles de disposition de la société.  
  
 Consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="gestures"></a>Mouvements  
 Vous pouvez définir des commandes que les utilisateurs exécutent en double-cliquant sur un élément de diagramme ou en faisant glisser sur un diagramme ou un élément du diagramme. Vous pouvez définir des commandes qui concernent des éléments déplacés à partir d’autres diagrammes UML, d’autres parties de Visual Studio ou d’autres applications ou l’Explorateur Windows (ou l’Explorateur de fichiers).  
  
 Les membres de l’équipe Fabrikam peuvent associer un fichier, tel qu’une spécification, à tout élément de modèle en le faisant glisser à partir du Bureau Windows. Les développeurs d’outils définissent un stéréotype qui fournit à tout élément une propriété de chemin d’accès de fichier, et un mouvement qui définit le stéréotype et le chemin d’accès quand un fichier est déposé sur un élément.  
  
 Pour plus d’informations, consultez [définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="responding-to-changes"></a>Réponse aux modifications  
 Vous pouvez écrire du code qui répond aux modifications apportées au modèle, qu’elles soient dues à des actions de l’utilisateur ou à un autre code de programme.  
  
 Les développeurs de Fabrikam créent du code qui définit automatiquement la couleur d’un élément en fonction de son stéréotype. Il est ainsi plus facile aux utilisateurs de distinguer les différents rôles joués par les éléments dans les modèles.  
  
 Pour plus d’informations, consultez [Comment : répondre aux modifications dans un modèle UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
## <a name="model-bus"></a>Bus de modèles  
 Le bus de modèles vous permet d'accéder à un diagramme ou à un modèle à partir d'un autre diagramme ou d'une autre Extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Cela vous permet entre autres de répartir les informations sur plusieurs modèles, pour que plusieurs personnes puissent travailler en même temps sur le modèle combiné.  
  
 Fabrikam utilise des éléments de diagrammes d’activités pour représenter l’équipement de manutention de bagages. Chaque élément de l’équipement peut avoir une spécification plus détaillée dans un autre diagramme, qui peut se trouver dans un autre modèle. Les contraintes de validation sur le diagramme de flux de bagages peuvent récupérer des propriétés pertinentes de l’équipement à partir des autres diagrammes. Les références aux autres diagrammes sont stockées dans des propriétés supplémentaires définies dans des stéréotypes.  
  
 Pour plus d’informations, consultez [intégrer des modèles UML avec d’autres modèles et outils](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
## <a name="generation"></a>Génération  
 À partir d’un modèle, vous pouvez générer du code de programme, des scripts, des configurations, des documents, de nouveaux modèles ou d’autres artefacts.  
  
 Dans les systèmes de bagages conçus par Fabrikam, la plupart du code de programme est identique d’un projet à l’autre. L’aspect le plus variable est le plan du flux de bagages autour de l’aéroport. Une fois que l’équipe de conception a tiré les enseignements de ses premiers projets, les développeurs d’outils créent un modèle qui génère, à partir du modèle de flux de bagages, une grande partie du code de programme variable et d’autres fichiers tels que les documents utilisateur. Cela réduit considérablement la durée de développement et le taux d’erreurs pour chaque nouveau projet.  
  
 Pour plus d’informations, consultez [générer des fichiers à partir d’un modèle UML](../modeling/generate-files-from-a-uml-model.md).  
  
## <a name="team-foundation-server-integration"></a>Intégration de Team Foundation Server  
 Vous pouvez lier des éléments de travail à des éléments de modèle et accéder aux éléments liés par programmation.  
  
 Les développeurs d’outils de Fabrikam écrivent un outil qui génère une planification du travail pour chaque projet d’aéroport. Les éléments de travail de la planification sont liés aux éléments de modèle.  
  
 Pour plus d’informations, consultez [définir un gestionnaire de liaison des éléments de travail](../modeling/define-a-work-item-link-handler.md).  
  
## <a name="tools-that-update-models"></a>Outils de mise à jour des modèles  
 Vous pouvez créer des extensions Visual Studio et des applications autonomes qui peuvent charger des modèles UML.  
  
 Les développeurs de Fabrikam créent un outil qui lit un modèle et génère des rapports sur la progression du travail sur chaque élément du modèle.  
  
 Pour plus d’informations, consultez [lire un modèle UML dans le code de programme](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="domain-specific-languages"></a>Langages spécifiques à un domaine  
 Quand vous utilisez fréquemment un type de modèle particulier, il peut être utile de créer un langage spécifique à un domaine. Vous pouvez l’adapter aux besoins de votre entreprise plus étroitement qu’un modèle UML, mais sa création et sa tenue à jour nécessitent davantage d’efforts. Pour plus d’informations, consultez [Modeling SDK pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="external-resources"></a>Ressources externes  
  
|**Catégorie**|**Liens**|  
|------------------|---------------|  
|**Vidéos**|![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") [série MSDN Comment faire : outils UML et extensibilité](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9 : UML with Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|  
|**Forums**|-   [Outils de visualisation et de modélisation Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling (outils DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|[Blog Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Articles et journaux techniques**|[Centre d’architecture MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)   
 [Informations de référence sur l’API pour l’extensibilité de la modélisation UML](../modeling/api-reference-for-uml-modeling-extensibility.md)



