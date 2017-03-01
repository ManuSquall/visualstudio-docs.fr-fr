---
title: "Diagrammes de dépendance : Indications | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 55
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 8233d0d6ce81a0869e99f5baf45b7ef7b3fc9019
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-guidelines"></a>Diagrammes de dépendance : instructions
Décrire l’architecture de votre application à un niveau élevé en créant *des diagrammes de dépendance* dans Visual Studio. Assurez-vous que votre code demeure conforme à cette conception en le validant avec un diagramme de dépendances. Vous pouvez également inclure la validation de couche dans votre processus de génération. Consultez la page [vidéo Channel 9 : conception et valider votre architecture à l’aide de diagrammes de dépendance](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Pour connaître les versions de Visual Studio prennent en charge cette fonctionnalité, consultez [prise en charge de Version pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>Qu’est un diagramme de dépendances ?  
 Comme un diagramme d’architecture traditionnel, un diagramme de dépendances identifie les principaux composants ou unités fonctionnelles de la conception et leurs interdépendances. Chaque nœud du diagramme, appelé un *couche*, représente un groupe logique d’espaces de noms, de projets ou d’autres artefacts. Vous pouvez dessiner les dépendances qui doivent exister dans votre conception. Contrairement à un diagramme d'architecture traditionnel, vous pouvez vérifier que les dépendances réelles dans le code source sont conformes aux dépendances prévues que vous avez spécifiées. En incluant la partie validation d'une build normale dans [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], vous pouvez vous assurer que le code du programme continue à respecter l'architecture du système au travers des modifications futures. Consultez la page [des diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md).  
  
##  <a name="a-nameupdatea-how-to-design-or-update-your-app-with-dependency-diagrams"></a><a name="Update"></a>Procédure pour concevoir ou mettre à jour votre application avec des diagrammes de dépendance  
 Les étapes suivantes fournissent une vue d’ensemble de l’utilisation des diagrammes de dépendance dans le processus de développement. Les sections suivantes de cette rubrique décrivent plus en détail chaque étape. Si vous développez une nouvelle conception, ignorez les étapes qui font référence au code existant.  
  
> [!NOTE]
>  Ces étapes s'affichent selon un ordre approximatif. Vous souhaiterez probablement superposer les tâches, les réorganiser en fonction de votre propre cas et les réexaminer au début de chaque itération de votre projet.  
  
1.  [Créer un diagramme de dépendance](#Create) pour l’application entière, ou pour une de ses couches.  
  
2.  [Définir des couches pour représenter les zones fonctionnelles principales ou composants](#CreateLayers) de votre application. Nommez ces couches d'après leur fonction, par exemple, « Présentation » ou « Services ». Si vous avez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solution, vous pouvez associer chaque couche à une collection de *artefacts*, tels que des projets, espaces de noms, fichiers et ainsi de suite.  
  
3.  [Découvrez les dépendances existantes](#Generate) entre les couches.  
  
4.  [Modifiez les couches et les dépendances](#EditArchitecture) pour afficher les mises à jour que vous souhaitez que le code afin de refléter de conception.  
  
5.  [Concevez des nouvelles zones de votre application](#NewAreas) en créant des couches pour représenter les composants ou blocs architecturaux principaux et définissant des dépendances pour montrer comment chaque couche utilise les autres.  
  
6.  [Modifier la disposition et l’apparence du diagramme](#EditLayout) pour vous aider à en discuter avec vos collègues.  
  
7.  [Valider le code par rapport au diagramme de dépendance](#Validate) pour mettre en évidence les conflits entre le code et l’architecture que vous avez besoin.  
  
8.  [Mettre à jour le code pour se conformer à la nouvelle architecture](#UpdateCode). Développez le code de manière itérative et refactorisez-le jusqu’à ce que la validation n’affiche aucun conflit.  
  
9. [Inclure la validation de couche dans le processus de génération](#BuildValidation) pour vous assurer que le code continue à respecter votre conception.  
  
##  <a name="a-namecreatea-create-a-dependency-diagram"></a><a name="Create"></a>Créer un diagramme de dépendance  
 Un diagramme de dépendance doit être créé à l’intérieur d’un projet de modélisation. Vous pouvez ajouter un nouveau diagramme de dépendance à un projet de modélisation existant, créez un nouveau projet de modélisation pour le diagramme de dépendances ou copier un diagramme de dépendance existant dans le même projet de modélisation.  
  
> [!IMPORTANT]
>  N’ajoutez pas, faites glisser ou copier un diagramme de dépendance existant à partir d’un projet de modélisation vers un autre projet de modélisation ou vers un autre emplacement dans la solution. Un diagramme de dépendances est copié de cette façon aura les mêmes références que le diagramme d’origine, même si vous modifiez le diagramme. La validation de couche ne peut alors fonctionner correctement et d’autres problèmes peuvent survenir, tels que l’absence d’éléments ou autre erreurs lors de l’ouverture du diagramme.  
  
 Consultez la page [créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="a-namecreatelayersa-define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a>Définir des couches pour représenter les composants ou les zones fonctionnelles  
 Couches représentent des groupes logiques de *artefacts*, tels que des projets, fichiers de code, espaces de noms, classes et méthodes. Vous pouvez créer des couches à partir d’artefacts de projets Visual C# .NET et Visual Basic .NET, ou vous pouvez attacher des spécifications ou des plans à une couche en liant des documents, tels que des fichiers Word ou des présentations PowerPoint. Chaque couche apparaît comme un rectangle sur le diagramme et indique le nombre d'artefacts qui lui sont liés. Une couche peut contenir des couches imbriquées qui décrivent des tâches plus spécifiques.  
  
 En règle générale, nommez les couches selon leur fonction : par exemple, « Présentation » ou « Services ». Si les artefacts sont étroitement interdépendants, placez-les dans la même couche. Si les artefacts peuvent être mis à jour séparément ou utilisés dans des applications distinctes, placez-les dans des couches différentes. Pour en savoir plus sur les modèles en couches, visitez le site de modèles et méthodes s’à [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Il existe certains types d’artefacts que vous pouvez lier aux couches mais qui ne prennent pas en charge validation par rapport au diagramme de dépendance. Pour voir si l’artefact prend en charge la validation, ouvrez **Explorateur de couches** pour examiner le **prend en charge la Validation** propriété du lien d’artefact. Consultez la page [découvrir les dépendances existantes entre des couches](#Generate).  
  
 Lors de la mise à jour d'une application peu familière, vous pouvez également créer des cartes de code. Ces diagrammes peuvent vous aider à découvrir des modèles et des dépendances quand vous explorez le code. Utilisez l'Explorateur de solutions pour explorer des espaces de noms et des classes, qui correspondent souvent à des couches existantes. Attribuer ces artefacts de code aux couches en les faisant glisser à partir de l’Explorateur de solutions pour les diagrammes de dépendance. Vous pouvez ensuite utiliser des diagrammes de dépendance pour vous aider à mettre à jour le code et d’assurer leur cohérence avec la conception de votre.  
  
 Reportez-vous à :  
  
-   [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="a-namegeneratea-discover-existing-dependencies-between-layers"></a><a name="Generate"></a>Découvrir les dépendances existantes entre les couches  
 Une dépendance existe chaque fois qu’un artefact associé à une couche comporte une référence à un artefact associé à une autre couche. Par exemple, une classe dans une couche déclare une variable qui a une classe dans une autre couche. Vous pouvez découvrir les dépendances existantes par rétroconception.  
  
> [!NOTE]
>  Les dépendances ne peuvent pas faire l'objet d'une ingénierie à rebours pour certains genres d'artefacts. Par exemple, aucune dépendance ne fera l'objet d'une ingénierie à rebours depuis ou vers une couche qui est liée à un fichier texte. Pour voir les artefacts ayant des dépendances que vous pouvez réaliser la rétroconception, cliquez sur une ou plusieurs couches, puis cliquez sur **afficher les liens**. Dans **Explorateur de couches**, examinez le **prend en charge la Validation** colonne. Dépendances ne sera pas à rebours pour les artefacts pour lesquels cette colonne affiche **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Pour procéder à la rétroconception des dépendances existantes entre couches  
  
-   Sélectionnez une ou plusieurs couches, cliquez sur une couche sélectionnée, puis cliquez sur **générer des dépendances**.  
  
 En général, des dépendances qui ne devraient pas exister s'affichent. Vous pouvez modifier ces dépendances pour les ajuster à la conception prévue.  
  
##  <a name="a-nameeditarchitecturea-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a>Modifier les couches et les dépendances pour afficher la conception prévue  
 Pour décrire les modifications que vous envisagez d’apporter à votre système ou de l’architecture prévue, procédez comme suit pour modifier le diagramme de dépendance. vous pouvez aussi envisager d'apporter des modifications de refactorisation pour améliorer la structure du code avant de l'étendre. Consultez la page [amélioration de la structure du code](#Improving).  
  
|**Pour**|**Procédez comme suit**|  
|------------|-----------------------------|  
|Supprimer une dépendance qui ne doit pas exister|Cliquez sur la dépendance, puis appuyez sur **supprimer**.|  
|Changer ou restreindre la direction d'une dépendance|Définir son **Direction** propriété.|  
|Créer de nouvelles dépendances|Utilisez le **dépendance** et **dépendance bidirectionnelle** tools.<br /><br /> Pour dessiner plusieurs dépendances, double-cliquez sur l'outil. Lorsque vous avez terminé, cliquez sur le **pointeur** outil ou appuyez sur la **ÉCHAP** clé.|  
|Spécifier que les artefacts associés à une couche ne peuvent pas dépendre des espaces de noms spécifiés|Tapez les espaces de noms dans la couche **interdit les dépendances Namespace** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
|Spécifier que les artefacts associés à une couche ne doivent pas appartenir aux espaces de noms spécifiés|Tapez les espaces de noms dans la couche **interdit les espaces de noms** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
|Spécifier que les artefacts associés à une couche doivent appartenir à un des espaces de noms spécifiés|Tapez l’espace de noms dans la couche **espace de noms requis** propriété. Utilisez un point-virgule (**;**) pour séparer les espaces de noms.|  
  
###  <a name="a-nameimprovinga-improving-the-structure-of-the-code"></a><a name="Improving"></a>Amélioration de la structure du code  
 Les modifications de refactorisation sont des améliorations qui n'affectent pas le comportement de l'application, mais qui contribuent à rendre le code plus facile à modifier et à étendre à l'avenir. Le code correctement structuré a une conception qu’il est facile de soustraire d’un diagramme de dépendances.  
  
 Par exemple, si vous créez une couche pour chaque espace de noms dans le code, puis soumettez les dépendances à une rétroconception, il doit exister un ensemble minimal de dépendances unidirectionnelles entre les couches. Si vous créez un diagramme plus détaillé à l'aide de classes ou de méthodes en tant que couches, le résultat doit également présenter les mêmes caractéristiques.  
  
 Si ce n’est pas le cas, le code sera plus difficile à modifier tout au long de son cycle de vie et sera moins adapté à la validation à l’aide de diagrammes de dépendance.  
  
##  <a name="a-namenewareasa-design-new-areas-of-your-application"></a><a name="NewAreas"></a>Concevez des nouvelles zones de votre application  
 Lorsque vous démarrez le développement d'un nouveau projet, ou d'une nouvelle partie d'un nouveau projet, vous pouvez dessiner des couches et des dépendances pour aider à identifier les principaux composants avant de commencer à développer le code.  
  
-   **Affichez des modèles architecturaux identifiables** dans vos diagrammes de dépendance, si possible. Par exemple, un diagramme de dépendances qui décrit une application bureautique peut inclure des couches telles que présentation, logique de domaine et magasin de données. Un diagramme de dépendance qui couvre une fonctionnalité unique au sein d’une application peut avoir des couches telles que modèle, vue et contrôleur. Pour plus d’informations sur ces modèles, consultez [modèles et méthodes se : Architecture de l’Application](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Si vous créez fréquemment des modèles similaires, créez un outil personnalisé. Consultez la page [définir un personnalisé élément de boîte à outils de modélisation](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Créez un artefact de code pour chaque couche** comme un espace de noms, une classe ou un composant. Il est ainsi plus facile de suivre le code et de lier les artefacts de code aux couches. Dès que vous créez un artefact, liez-le à la couche appropriée.  
  
-   **Vous n’avez pas à lier la plupart des classes et autres artefacts aux couches** , car ils font partie d’artefacts plus importants tels que les espaces de noms que vous avez déjà liés aux couches.  
  
-   **Créer un nouveau diagramme pour une nouvelle fonctionnalité**. En règle générale, il y aura un ou plusieurs diagrammes de dépendance décrivant l’application entière. Si vous concevez une nouvelle fonctionnalité dans l’application, ne modifiez pas les diagrammes existants ou ne la leur ajoutez pas. Créez à la place votre propre diagramme qui reflète les nouvelles parties du code. Les couches du nouveau diagramme peuvent inclure la présentation, la logique de domaine et les couches de base de données pour la nouvelle fonctionnalité.  
  
     Lorsque vous générez l’application, votre code est validé par rapport au diagramme global et à votre diagramme de fonctionnalités détaillé.  
  
##  <a name="a-nameeditlayouta-edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a>Modifier la disposition pour la présentation et la discussion  
 Pour vous aider à identifier des couches et des dépendances ou à en discuter avec les membres de l’équipe, modifiez l’aspect et la disposition du diagramme comme suit :  
  
-   Modifiez les tailles, formes et positions des couches.  
  
-   Modifiez les couleurs des couches et des dépendances.  
  
    -   Sélectionnez une ou plusieurs couches ou dépendances, avec le bouton droit, puis cliquez sur **propriétés**. Dans le **propriétés** fenêtre, modifiez la **couleur** propriété.  
  
##  <a name="a-namevalidatea-validate-the-code-against-the-diagram"></a><a name="Validate"></a>Valider le code par rapport au diagramme  
 Quand vous avez modifié le diagramme, vous pouvez le valider manuellement par rapport au code à tout moment ou automatiquement chaque fois que vous exécutez une génération locale ou [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].  
  
 Reportez-vous à :  
  
-   [Valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Inclure la Validation de couche dans le processus de génération](#BuildValidation)  
  
##  <a name="a-nameupdatecodea-update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a>Mise à jour le code pour se conformer à la nouvelle architecture  
 En général, les erreurs apparaissent la première fois que vous validez le code par rapport à un diagramme de dépendance mis à jour. Ces erreurs peuvent avoir plusieurs causes :  
  
-   Un artefact est assigné à une couche inappropriée. Dans ce cas, déplacez l'artefact.  
  
-   Un artefact, tel qu'une classe, utilise une autre classe d'une manière qui génère un conflit avec votre architecture. Dans ce cas, refactorisez le code pour supprimer la dépendance.  
  
 Pour résoudre ces erreurs, mettez à jour le code de façon à ce que la validation ne génère plus d'erreur. Il s'agit généralement d'un processus itératif. Pour plus d’informations sur ces erreurs, consultez la page [valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Lorsque vous développez ou refactorisez le code, vous pouvez avoir des nouveaux artefacts à lier au diagramme de dépendance. Toutefois, cela peut ne pas être nécessaire : par exemple, lorsque des couches représentent des espaces de noms existants et que le nouveau code ajoute seulement plus de documentation à ces espaces de noms.  
  
 Pendant le processus de développement, vous pouvez supprimer certains conflits signalés pendant la validation. Par exemple, vous pouvez supprimer des erreurs que vous êtes déjà en train de traiter qui ne sont pas pertinentes dans le cadre de votre scénario spécifique. Lorsque vous supprimez une erreur, il est conseillé d'entrer un élément de travail dans [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Pour effectuer cette tâche, consultez [valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="a-namebuildvalidationa-include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a>Inclure la validation de couche dans le processus de génération  
 Pour vous assurer que les futures modifications dans le code sont conformes aux diagrammes de dépendance, inclure la validation de couche au processus de génération standard de votre solution. Chaque fois que les autres membres de l’équipe génèrent la solution, les différences entre les dépendances dans le code et le diagramme de dépendances seront signalées comme erreurs de build. Pour plus d’informations sur l’inclusion de la validation de couche dans le processus de génération, consultez [valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)   
 [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)

