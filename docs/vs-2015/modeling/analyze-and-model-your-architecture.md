---
title: Analyser et modéliser votre architecture | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 129
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b7d7f9f478e85229eaa72ab04d12b6b542cbab5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781034"
---
# <a name="analyze-and-model-your-architecture"></a>Analyser et modéliser votre architecture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Faites-en sorte que votre application respecte les spécifications de l’utilisateur en utilisant les outils d’architecture et de modélisation de Visual Studio pour concevoir et modéliser votre application. Appréhendez le code de programme existant plus facilement en utilisant Visual Studio pour visualiser la structure, le comportement et les relations du code.  
  
 Créez des modèles à différents niveaux de détails tout au long du cycle de vie de l’application dans le cadre de votre processus de développement. Suivez les spécifications, les tâches, les cas de test, les bogues et les autres travaux associés à vos modèles, en liant des éléments de modèle à des éléments de travail Team Foundation Server et à votre plan de développement. Consultez [scénario : modifier votre conception à l’aide de la visualisation et modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
 Pour connaître les versions de Visual Studio qui prennent en charge chaque fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="to"></a>À  
  
|||  
|-|-|  
|**Visualiser du code**:<br /><br /> -Consultez organisation et les relations du code en créant des cartes de code. Visualisez les dépendances entre les assemblys, les espaces de noms, les classes, les méthodes et ainsi de suite.<br />-Consultez la structure des classes et membres d’un projet spécifique en créant des diagrammes de classes à partir de code.<br />-Recherchez des conflits entre votre code et sa conception en créant des diagrammes de couche pour valider le code.<br /><br /> **Remarque**: dans cette version de Visual Studio, le terme *carte de code* est utilisé à la place de *graphique de dépendance*. Le terme *graphique* utilisé seul se réfère généralement à un graphique orienté ou diagramme (document) DGML. Les cartes de code sont un type spécialisé de diagramme DGML.|-   [Visualiser du code](../modeling/visualize-code.md)<br />-   [Utilisation des Classes et d’autres Types (Concepteur de classes)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vidéo : Comprendre les dépendances dans votre code grâce à la visualisation (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Vidéo : Visualiser l’impact d’une modification (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|  
|**Décrire et communiquer les spécifications des utilisateurs**:<br /><br /> -Clarifier les récits utilisateur, les règles d’entreprise et les autres exigences et garantir leur cohérence en dessinant des diagrammes UML tels que les cas d’usage, l’activité et des diagrammes de classes.|-   [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)<br />-   [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)<br />-   [Vidéo : Améliorer l’architecture grâce à la modélisation (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|  
|**Définir l’architecture**:<br /><br /> -Modèle de la structure à grande échelle de votre système logiciel et les modèles de conception en dessinant des diagrammes de séquence, la classe et composant UML.<br />-Permet de définir et appliquer des contraintes sur les dépendances entre les composants de votre code en créant des diagrammes de couche.|-   [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)<br />-   [Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)<br />-   [Vidéo : Améliorer l’architecture grâce à la modélisation (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Vidéo : Utiliser des diagrammes de couche pour concevoir et valider votre architecture (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Valider votre système avec les spécifications et la conception prévue**<br /><br /> -Définir les tests d’acceptation ou des tests système basés sur les modèles d’impératifs. Ainsi, une relation forte entre les tests et les spécifications de vos utilisateurs est créée et vous aide à mettre à jour le système plus facilement quand les spécifications changent.<br />-Valider les dépendances de code avec des diagrammes de couche qui décrivent l’architecture prévue et empêchent les modifications pouvant entrer en conflit avec la conception.|-   [Valider votre système pendant le développement](../modeling/validate-your-system-during-development.md)<br />-   [Vidéo : Utiliser des diagrammes de couche pour concevoir et valider votre architecture (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|  
|**Partager des modèles, des diagrammes et des cartes de code à l’aide du contrôle de version Team Foundation**:<br /><br /> -Placez des cartes de code et projets de modélisation, des diagrammes UML, les diagrammes de couche sous contrôle de version Team Foundation afin de pouvoir les partager.|Quand vous avez plusieurs utilisateurs qui travaillent avec ces éléments sous contrôle de version Team Foundation, utilisez ces instructions pour éviter les problèmes liés au contrôle de version :<br /><br /> -   [Gérer des modèles et des diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Générer ou configurer certaines parties de votre application à partir de langages UML ou propres à un domaine**:<br /><br /> -Rendre votre conception plus réactive aux modifications d’exigences et rendez-la facilement variable sur une gamme de produits.|-   [Générer et configurer votre application à partir de modèles](../modeling/generate-and-configure-your-app-from-models.md)|  
|**Personnaliser des modèles et des diagrammes**:<br /><br /> -Adapter des modèles à la manière dont votre projet les utilise en définissant des propriétés supplémentaires pour les éléments UML, contraintes de validation pour vous assurer que vos modèles sont conformes à vos règles d’entreprise et les commandes de menu supplémentaires et les éléments de boîte à outils.<br />-Créer vos propres langages spécifiques à un domaine.|-   [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [SDK Modeling pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Générer du texte à l’aide de modèles T4**:<br /><br /> -Utilisez les blocs de texte et la logique de contrôle à l’intérieur des modèles pour générer des fichiers texte.|-   [Génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)|  
  
## <a name="types-of-models-and-their-uses"></a>Types de modèles et leurs utilisations  
  
|**Type de modèle et utilisations courantes**|  
|-------------------------------------|  
|**Cartes de code**<br /><br /> Les cartes de code vous aident à voir l’organisation et les relations dans votre code.<br /><br /> Utilisations courantes :<br /><br /> -Examiner le code de programme afin de mieux comprendre sa structure et ses dépendances, comment mettre à jour et estimer le coût des modifications proposées.<br /><br /> Consultez :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Rechercher des problèmes potentiels à l’aide des analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Diagramme de couche**<br /><br /> Les diagrammes de couche vous permettent de définir la structure d’une application en tant qu’ensemble de couches ou de blocs avec des dépendances explicites. Vous pouvez exécuter la validation pour détecter les conflits entre les dépendances dans le code et celles décrites dans un diagramme de couche.<br /><br /> Utilisations courantes :<br /><br /> -Stabiliser la structure de l’application via de nombreuses modifications pendant sa durée de vie.<br />-Détecter les conflits de dépendance involontaires avant d’archiver les modifications apportées au code.<br /><br /> Consultez :<br /><br /> -   [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de couche : référence](../modeling/layer-diagrams-reference.md)<br />-   [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)|  
|**Modèle UML**<br /><br /> Un modèle UML comprend plusieurs vues, notamment des diagrammes de classes, de composants, de cas d’usage, d’activité et de séquence. Vous pouvez personnaliser un modèle UML pour l’adapter à votre domaine d’application. Par exemple, vous pouvez joindre des balises, des informations supplémentaires et des contraintes aux éléments de modèle. Vous pouvez également définir des outils qui fonctionnent sur les modèles. Consultez [créer des modèles pour votre application](../modeling/create-models-for-your-app.md).<br /><br /> Utilisations courantes :<br /><br /> -Décrivent les spécifications et la conception. Vous pouvez appliquer rapidement un modèle UML au développement d’une application. Consultez [utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md).<br />-Générer ou configurer des tests ou des parties d’une application. Un travail est requis pour personnaliser la notation et développer les modèles de génération ou l’application configurable. Consultez [générer et configurer votre application à partir de modèles](../modeling/generate-and-configure-your-app-from-models.md).<br />-Pour une description générale et pour la génération de code ou de configuration dans les projets plus petits.|  
|**Langage spécifique à un domaine (DSL)**<br /><br /> Un langage spécifique à un domaine est une notation que vous concevez dans un but spécifique. Dans Visual Studio, il est en général graphique.<br /><br /> Utilisations courantes :<br /><br /> -Générer ou configurer certaines parties de l’application. Un travail est requis pour développer la notation et les outils. Le résultat est ainsi plus adapté à votre domaine qu’une personnalisation UML.<br />-Pour les grands projets ou dans des gammes de produits où l’investissement dans le développement de la solution DSL et ses outils est amorti par son utilisation dans plusieurs projets.<br /><br /> Consultez :<br /><br /> -   [SDK Modeling pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Où peut-on obtenir plus d’informations ?  
  
|||  
|-|-|  
|**Forums**|-   [Outils de visualisation et de modélisation Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling (outils DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [DevOps et Application Lifecycle Management](http://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)



