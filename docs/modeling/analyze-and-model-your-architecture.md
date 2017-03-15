---
title: "Analyser et modéliser votre architecture | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>Analyser et modéliser votre architecture
Assurez-vous que votre application répond aux spécifications architecturales à l’aide de l’architecture Visual Studio et outils pour concevoir et modéliser votre application de modélisation. 

* Appréhendez le code de programme existant plus facilement en utilisant Visual Studio pour visualiser la structure, le comportement et les relations du code. 

* Formez votre équipe dans la nécessité de respecter des dépendances architecturales.  
  
* Créez des modèles à différents niveaux de détails tout au long du cycle de vie de l’application dans le cadre de votre processus de développement.

Consultez la page [scénario : modifier votre conception à l’aide de la visualisation et de modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
## <a name="to"></a>À  
  
|||  
|-|-|  
|**Visualiser du code**:<br /><br /> -Consultez organisation et les relations du code en créant des cartes de code. Visualisez les dépendances entre les assemblys, les espaces de noms, les classes, les méthodes et ainsi de suite.<br />-Voir la structure des classes et membres d’un projet spécifique en créant des diagrammes de classes à partir de code.<br />-Recherchez des conflits entre votre code et sa conception en créant des diagrammes de dépendance pour valider le code.|-   [Visualiser le code](../modeling/visualize-code.md)<br />-   [Utilisation des Classes et d’autres Types (Concepteur de classes)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vidéo : Comprendre la conception du code avec Visual Studio 2015 code maps](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Vidéo : Valider les dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**Définir l’architecture**:<br /><br /> -Permet de définir et d’appliquer des contraintes sur les dépendances entre les composants de votre code en créant des diagrammes de dépendance.|-   [Vidéo : Valider les dépendances d’architecture avec Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Valider votre système avec les spécifications et la conception prévue :**<br /><br /> -Permet de contrôler les dépendances de code avec des diagrammes de dépendance qui décrivent l’architecture prévue et empêchent les modifications entrent en conflit avec la conception.|-   [Vidéo : Valider les dépendances d’architecture avec Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Partager des modèles, des diagrammes et des cartes de code à l’aide du contrôle de version Team Foundation**:<br /><br /> -Placer des cartes de code, projets et diagrammes deoendency sous contrôle de version Team Foundation afin de les partager.|Quand vous avez plusieurs utilisateurs qui travaillent avec ces éléments sous contrôle de version Team Foundation, utilisez ces instructions pour éviter les problèmes liés au contrôle de version :<br /><br /> -   [Gérer des modèles et des diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Personnaliser des modèles et des diagrammes**:<br /><br /> -Permet de créer vos propres langages spécifiques au domaine.|-   [Modélisation du Kit de développement logiciel pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Générer du texte à l’aide de modèles T4**:<br /><br /> -Utilisez les blocs de texte et de logique de contrôle à l’intérieur des modèles pour générer des fichiers texte.<br /> -Génération de modèle T4 avec MSBuild inclus dans Visual Studio|-   [Génération de code et de modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)|

Pour connaître les versions de Visual Studio prennent en charge chaque fonctionnalité, consultez [Version prise en charge pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>Types de modèles et leurs utilisations  
  
|**Type de modèle et utilisations courantes**|  
|-------------------------------------|  
|**Cartes de code**<br /><br /> Les cartes de code vous aident à voir l’organisation et les relations dans votre code.<br /><br /> Utilisations courantes :<br /><br /> -Examiner le code du programme afin de mieux comprendre sa structure et ses dépendances, comment mettre à jour et estimer le coût des modifications proposées.<br /><br /> Reportez-vous à :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Utilisez des cartes de code à déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Rechercher des problèmes potentiels à l’aide des analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagramme de dépendances**<br /><br /> Diagrammes de dépendance vous permettent de définir la structure d’une application en tant qu’ensemble de couches ou de blocs avec des dépendances explicites. Vous pouvez exécuter la validation pour détecter les conflits entre les dépendances dans le code et décrites dans un diagramme de dépendance.<br /><br /> Utilisations courantes :<br /><br /> -Stabiliser la structure de l’application via de nombreuses modifications sur sa durée.<br />-Détecter les conflits de dépendance involontaires avant d’archiver les modifications du code.<br /><br /> Reportez-vous à :<br /><br /> -   [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)<br />-   [Valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)|  
|**Langage spécifique au domaine (DSL)**<br /><br /> Un langage spécifique à un domaine est une notation que vous concevez dans un but spécifique. Dans Visual Studio, il est en général graphique.<br /><br /> Utilisations courantes :<br /><br /> -Générer ou configurer certaines parties de l’application. Un travail est requis pour développer la notation et les outils. Le résultat est ainsi plus adapté à votre domaine qu’une personnalisation UML.<br />-Pour les grands projets ou dans des gammes de produits où l’investissement dans le développement du langage DSL et ses outils est retourné par son utilisation dans plusieurs projets.<br /><br /> Reportez-vous à :<br /><br /> -   [Modélisation du Kit de développement logiciel pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Q : Où puis-je obtenir plus d’informations ?  
  
[Visual Studio Visualization se Forum des outils de modélisation](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [Opérations de développement et de gestion du cycle de vie des applications](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

