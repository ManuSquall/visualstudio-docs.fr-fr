---
title: Personnalisation de l’Explorateur de modèles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eb0b8b58d133a26c7970071b422e0c20f42c063
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433234"
---
# <a name="customizing-the-model-explorer"></a>Personnalisation de l'Explorateur de modèles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier l’apparence et le comportement de l’Explorateur pour votre Concepteur de langage spécifique à un domaine comme suit :  
  
- Modifier le titre de fenêtre.  
  
- Modifier l’icône d’onglet.  
  
- Modifier les icônes pour les nœuds.  
  
- Masquer les nœuds.  
  
## <a name="changing-the-window-title"></a>Modification du titre de fenêtre  
 Pour modifier le titre de la fenêtre de l’Explorateur généré, sélectionnez **comportement de l’Explorateur** dans le **Explorateur DSL**, puis, dans le **propriétés** fenêtre, définissez la  **Titre** propriété pour le titre de votre choix.  
  
## <a name="changing-the-tab-icon"></a>Modification de l’icône d’onglet  
 Pour modifier l’icône d’onglet de l’Explorateur, utiliser une icône de 16 x 16 pixels dans un fichier .bmp. Placez le fichier d’icône dans le dossier \DslPackage\Resources\, puis remplacez le nom de fichier par **ModelExplorerToolWindowBitmaps.bmp**. Par exemple, vous pouvez modifier le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] setup.ico icône fichier au format .bmp et renommez-le **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. Le concepteur généré affiche cette icône sous l’onglet de votre Explorateur lorsqu’elle est ancrée avec **l’Explorateur de solutions**.  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>Définition des icônes personnalisées sur les nœuds de l’Explorateur  
 Vous pouvez personnaliser les nœuds dans votre Explorateur à l’aide des paramètres de nœud de l’Explorateur. La procédure suivante montre comment ajouter une icône à un nœud.  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>Pour ajouter une icône pour un nœud de l’Explorateur  
  
1. Créer un [!INCLUDE[dsl](../includes/dsl-md.md)] solution à l’aide du modèle de solution flux de tâches.  
  
2. Placez un fichier .bmp qui contient une icône de 16 x 16 pixels dans le **Dsl\Resources** dossier dans la solution.  
  
3. Dans le **Explorateur DSL**, avec le bouton droit **comportement de l’Explorateur** puis cliquez sur **ajouter de nouveaux Explorer nœud paramètres**.  
  
     Un **ExplorerNodeSettings** nœud apparaît sous la **des paramètres de nœud personnalisés** nœud.  
  
4. Sélectionnez **ExplorerNodeSettings**, puis, dans le **propriétés** fenêtre, définissez **classe** à **acteur**.  
  
5. Définissez **affichage de l’icône à** pour le chemin d’accès du fichier icône.  
  
6. Transformer tous les modèles, puis générer et exécuter la solution.  
  
7. Dans le concepteur généré, ouvrez l’exemple de diagramme.  
  
     L’Explorateur doit montrer que trois **acteur** nœuds ayant votre icône.  
  
> [!NOTE]
> Si vous avez défini une icône de nœud pour tout élément qui s’affiche dans l’Explorateur généré, tous les nœuds de l’Explorateur affiche l’icône. Si aucune icône n’a été défini, les nœuds seront affichent l’icône par défaut.  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Modification du nom affiché sur un nœud de l’Explorateur  
 Vous pouvez modifier la façon dont les noms d’éléments de modèle sont affichés dans l’Explorateur de. La procédure suivante montre comment afficher le nom de la **tâche** qui est référencé par une **commentaire** dans le nœud de commentaire.  
  
#### <a name="to-display-a-property"></a>Pour afficher une propriété  
  
1. Ouvrez la solution que vous avez créé dans la procédure précédente.  
  
2. Assurez-vous que le **commentaire** fait référence à une classe de domaine unique en définissant la multiplicité du rôle avec le nom de la propriété **sujets** 0.. 1. Le nom de propriété doit devenir **sujet**, et le nom de la relation doit devenir **CommentReferencesSubject**.  
  
3. Dans le **Explorateur DSL**, avec le bouton droit **comportement de l’Explorateur** puis cliquez sur **ajouter de nouveaux Explorer nœud paramètres**.  
  
     Un **ExplorerNodeSettings** nœud apparaît sous la **des paramètres de nœud personnalisés** nœud.  
  
4. Sélectionnez **ExplorerNodeSettings**, puis, dans le **propriétés** fenêtre, définissez **classe** à **commentaire**.  
  
5. Cliquez sur le **commentaire** nœud, puis cliquez sur **ajouter un nouveau chemin de propriété**.  
  
     Un nouveau nœud apparaît nommé **propriété affichée**.  
  
6. Sélectionnez **propriété affichée**, puis, dans le **propriétés** fenêtre, cliquez sur le champ de valeur **chemin d’accès à la propriété**. Sélectionnez **commentaire**, puis **CommentReferencesSubject**, puis **FlowElement**. Le chemin d’accès résultant doit ressembler à **CommentReferencesSubject.Subject/ ! Objet**.  
  
7. Dans le champ de valeur **propriété**, sélectionnez **nom**.  
  
8. Transformer tous les modèles, puis générer et exécuter votre solution.  
  
9. Dans le concepteur généré, ouvrez l’exemple de diagramme.  
  
10. Dessiner un **commentaire connecteur** entre l’élément de commentaire et **Task1** élément du diagramme.  
  
     Le nœud de l’Explorateur doit afficher le commentaire sous la forme **Task1**.  
  
## <a name="hiding-nodes"></a>Masquer des nœuds  
 Vous pouvez masquer un nœud dans l’Explorateur en ajoutant son chemin d’accès à la **nœuds masqués** nœud de la **Explorateur DSL**. La procédure suivante montre comment masquer **commentaire** nœuds.  
  
#### <a name="to-hide-an-explorer-node"></a>Pour masquer un nœud de l’Explorateur  
  
1. Ouvrez la solution que vous avez créé dans la procédure précédente.  
  
2. Dans le **Explorateur DSL**, avec le bouton droit **comportement de l’Explorateur** puis cliquez sur **ajouter un nouveau chemin de domaine**.  
  
     Un **chemin d’accès du domaine** nœud apparaît sous **nœuds masqués**.  
  
3. Sélectionnez **chemin d’accès du domaine**, puis, dans le **propriétés** fenêtre, cliquez sur le champ de valeur **définition du chemin d’accès**. Sélectionnez **FlowGraph**, puis **FlowGraphHasComments**. Le chemin d’accès résultant doit ressembler à **FlowGraphHasComments.Comments**  
  
4. Transformer tous les modèles, puis générer et exécuter votre solution.  
  
5. Dans le concepteur généré, ouvrez l’exemple de diagramme.  
  
     L’Explorateur doit afficher uniquement une **acteurs** nœud et ne doit pas afficher le **commentaires** nœud.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des Outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
