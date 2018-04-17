---
title: Personnalisation de l’Explorateur de modèles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c69cdd822941fd81478fae0b62d509b64ef513da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-the-model-explorer"></a>Personnalisation de l'Explorateur de modèles
Vous pouvez modifier l’apparence et le comportement de l’Explorateur de votre Concepteur de langage spécifique à un domaine comme suit :  
  
-   Modifier le titre de la fenêtre.  
  
-   Modifier l’icône d’onglet.  
  
-   Modifier les icônes pour les nœuds.  
  
-   Masquer les nœuds.  
  
## <a name="changing-the-window-title"></a>Modification du titre de fenêtre  
 Pour modifier le titre de la fenêtre de l’Explorateur généré, sélectionnez **comportement de l’Explorateur de** dans les **Explorateur DSL**, puis, dans le **propriétés** , configurez le  **Titre** propriété pour le titre de votre choix.  
  
## <a name="changing-the-tab-icon"></a>Modification de l’icône d’onglet  
 Pour modifier l’icône de l’onglet de l’Explorateur, utilisent une icône de 16 x 16 pixels dans un fichier .bmp. Placez le fichier d’icône dans le dossier \DslPackage\Resources\, puis modifiez le nom de fichier à **ModelExplorerToolWindowBitmaps.bmp**. Par exemple, vous pouvez modifier le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico icône de fichier au format .bmp et renommez-la **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Le concepteur généré affiche cette icône sous l’onglet de l’Explorateur de votre lorsqu’elle est ancrée avec **l’Explorateur de solutions**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Définition d’icônes personnalisées sur les nœuds de l’Explorateur  
 Vous pouvez personnaliser les nœuds dans l’Explorateur de votre à l’aide des paramètres de nœud de l’Explorateur. La procédure suivante montre comment ajouter une icône à un nœud.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Pour ajouter une icône pour un nœud de l’Explorateur  
  
1.  Créer un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solution à l’aide du modèle de solution de flux de tâches.  
  
2.  Placez un fichier .bmp qui contient une icône de 16 x 16 pixels dans les **Dsl\Resources** dossier dans la solution.  
  
3.  Dans le **Explorateur DSL**, avec le bouton droit **Explorer comportement** puis cliquez sur **ajouter des paramètres de nœud de l’Explorateur de nouveau**.  
  
     Un **ExplorerNodeSettings** nœud apparaît sous la **configuration personnalisée du nœud** nœud.  
  
4.  Sélectionnez **ExplorerNodeSettings**, puis, dans le **propriétés** , configurez **classe** à **acteur**.  
  
5.  Définissez **icône à afficher** pour le chemin d’accès du fichier icône.  
  
6.  Transformer tous les modèles, puis créer et exécuter la solution.  
  
7.  Dans le concepteur généré, ouvrez l’exemple de diagramme.  
  
     L’Explorateur doit afficher trois **acteur** nœuds ayant l’icône.  
  
> [!NOTE]
>  Si vous avez défini une icône de nœud pour tout élément qui est affiché dans l’Explorateur généré, tous les nœuds de l’Explorateur affiche l’icône. Si aucune icône n’a été défini, les nœuds affiche l’icône par défaut.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>La modification du nom affiché sur un nœud de l’Explorateur  
 Vous pouvez modifier la façon dont les noms des éléments de modèle sont affichés dans l’Explorateur de votre. La procédure suivante montre comment afficher le nom de la **tâche** qui est référencé par une **commentaire** dans le nœud de commentaire.  
  
#### <a name="to-display-a-property"></a>Pour afficher une propriété  
  
1.  Ouvrez la solution que vous avez créé dans la procédure précédente.  
  
2.  Assurez-vous que le **commentaire** fait référence à une classe de domaine unique en définissant la multiplicité du rôle avec le nom de la propriété **sujets** 0.. 1. Le nom de propriété doit devenir **sujet**, et le nom de la relation doit devenir **CommentReferencesSubject**.  
  
3.  Dans le **Explorateur DSL**, avec le bouton droit **Explorer comportement** puis cliquez sur **ajouter des paramètres de nœud de l’Explorateur de nouveau**.  
  
     Un **ExplorerNodeSettings** nœud apparaît sous la **configuration personnalisée du nœud** nœud.  
  
4.  Sélectionnez **ExplorerNodeSettings**, puis, dans le **propriétés** , configurez **classe** à **commentaire**.  
  
5.  Cliquez sur le **commentaire** nœud, puis cliquez sur **ajouter un nouveau chemin de propriété**.  
  
     Un nouveau nœud apparaît nommé **propriété affichée**.  
  
6.  Sélectionnez **propriété affichée**, puis, dans le **propriétés** fenêtre, cliquez sur le champ de valeur de **chemin d’accès à la propriété**. Sélectionnez **commentaire**, puis **CommentReferencesSubject**, puis **élément FlowElement**. Le chemin d’accès qui en résulte doit ressembler à **CommentReferencesSubject.Subject/ ! Objet**.  
  
7.  Dans le champ de valeur de **propriété**, sélectionnez **nom**.  
  
8.  Transformer tous les modèles, puis créer et exécuter votre solution.  
  
9. Dans le concepteur généré, ouvrez l’exemple de diagramme.  
  
10. Dessiner un **commentaire connecteur** entre l’élément et la **Task1** élément du diagramme.  
  
     Le nœud de l’Explorateur doit afficher le commentaire **Task1**.  
  
## <a name="hiding-nodes"></a>Le masquage des nœuds  
 Vous pouvez masquer un nœud dans l’Explorateur de votre en ajoutant son chemin d’accès à la **masqué de nœuds** nœud de la **Explorateur DSL**. La procédure suivante montre comment masquer **commentaire** nœuds.  
  
#### <a name="to-hide-an-explorer-node"></a>Pour masquer un nœud de l’Explorateur  
  
1.  Ouvrez la solution que vous avez créé dans la procédure précédente.  
  
2.  Dans le **Explorateur DSL**, avec le bouton droit **Explorer comportement** puis cliquez sur **ajouter un nouveau chemin de domaine**.  
  
     A **chemin d’accès du domaine** nœud apparaît sous **masqué des nœuds**.  
  
3.  Sélectionnez **chemin d’accès du domaine**, puis, dans le **propriétés** fenêtre, cliquez sur le champ de valeur de **définition du chemin d’accès**. Sélectionnez **FlowGraph**, puis **FlowGraphHasComments**. Le chemin d’accès qui en résulte doit ressembler à **FlowGraphHasComments.Comments**  
  
4.  Transformer tous les modèles, puis créer et exécuter votre solution.  
  
5.  Dans le concepteur généré, ouvrez l’exemple de diagramme.  
  
     L’Explorateur doit uniquement afficher une **acteurs** nœud et ne doit pas afficher le **commentaires** nœud.  
  
## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)