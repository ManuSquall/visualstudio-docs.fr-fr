---
title: "Personnalisation de l&#39;Explorateur de mod&#232;les | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.explorerbehavior"
helpviewer_keywords: 
  - "outils de langage spécifique à un domaine, explorateur de langage spécifique à un domaine"
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Personnalisation de l&#39;Explorateur de mod&#232;les
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez modifier l'apparence et le comportement de l'explorateur pour votre concepteur de langage spécifique au domaine comme suit :  
  
-   Modifiez le titre de la fenêtre.  
  
-   modifiez l'icône d'onglet.  
  
-   Modifiez les icônes pour les nœuds.  
  
-   Masquer les nœuds.  
  
## Modifier le titre de la fenêtre  
 Pour modifier le titre de la fenêtre de l'explorateur généré, sélectionnez **Comportement de l'explorateur** dans **Explorateur DÉSOLÉ**, puis dans la fenêtre de **Propriétés** , affectez à la propriété de **Title** dans le titre que vous souhaitez.  
  
## modifier l'icône d'Onglet  
 Pour modifier l'icône d'onglet de l'explorateur, utilisez une icône de 16 x 16 pixels dans un fichier .bmp.  Mettez le fichier icône dans \\DslPackage\\Resources\\ folder, and then change the file name to ModelExplorerToolWindowBitmaps .bmp.  Par exemple, vous pouvez modifier le fichier icône de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] setup.ico au format .bmp\) et le renommer à DSLLanguageName \\DslPackage\\Resources\\ModelExplorerToolWindowBitmaps .bmp.  Le concepteur généré affiche cette icône sous l'onglet de votre explorateur lorsqu'il est ancré avec **Explorateur de solutions**.  
  
## Images personnalisées de paramètre sur des nœuds de l'explorateur  
 Vous pouvez personnaliser des nœuds dans votre explorateur à l'aide de les paramètres de nœud de l'explorateur.  La procédure suivante montre comment ajouter une icône à un nœud.  
  
#### Pour ajouter une icône à un nœud de l'explorateur  
  
1.  Créez une solution de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] à l'aide de le modèle de solution de flux de travail.  
  
2.  Placez un fichier .bmp qui contient une icône de 16 x 16 pixels dans le dossier de **DÉSOLÉ \\Resources** dans la solution.  
  
3.  Dans **Explorateur DÉSOLÉ**, cliquez avec le bouton droit sur **Comportement de l'explorateur** puis cliquez sur **Ajoutez les nouveaux paramètres de nœud de l'explorateur**.  
  
     Un nœud d' **ExplorerNodeSettings** s'affiche sous le nœud de **Paramètres personnalisés de nœud** .  
  
4.  Sélectionnez **ExplorerNodeSettings**, puis dans la fenêtre de **Propriétés** , définit **Classe** à **Acteur**.  
  
5.  Définissez **Icône à afficher** au chemin d'accès du fichier icône.  
  
6.  Transformez tous les modèles, puis générez et exécutez la solution.  
  
7.  Dans le concepteur généré, ouvrez le diagramme d'exemple.  
  
     L'explorateur doit afficher trois nœuds d' **Acteur** qui ont votre icône.  
  
> [!NOTE]
>  Si vous avez défini une icône de nœud pour tout élément affiché dans l'explorateur généré, tous les nœuds de l'explorateur affichent l'icône.  Si aucune icône n'a été définie, les nœuds affichent l'icône par défaut.  
  
## La modification du nom affiché sur un nœud de l'explorateur  
 Vous pouvez modifier la façon dont les noms d'éléments de modèle sont affichés dans votre explorateur.  La procédure suivante indique comment afficher le nom de la tâche qui est référencée par un commentaire dans le nœud de commentaire.  
  
#### pour afficher une propriété  
  
1.  Ouvrez la solution que vous avez créée dans la procédure antérieure.  
  
2.  Assurez \-vous que le commentaire référence qu'une seule classe de domaine en définissant la multiplicité du rôle du nom de la propriété **Sujets** à 0..1.  Le nom de la propriété doit être **Objet**, et le nom de la relation doit être **CommentReferencesSubject**.  
  
3.  Dans **Explorateur DÉSOLÉ**, cliquez avec le bouton droit sur **Comportement de l'explorateur** puis cliquez sur **Ajoutez les nouveaux paramètres de nœud de l'explorateur**.  
  
     Un nœud d' **ExplorerNodeSettings** s'affiche sous le nœud de **Paramètres personnalisés de nœud** .  
  
4.  Sélectionnez **ExplorerNodeSettings**, puis dans la fenêtre de **Propriétés** , définit **Classe** à **Commentaire**.  
  
5.  Cliquez avec le bouton droit sur le nœud de **Commentaire** , puis cliquez sur **ajoutez le nouveau chemin de propriété**.  
  
     Un nouveau nœud apparaît nommé **propriété affichée**.  
  
6.  Sélectionnez **propriété affichée**, puis dans la fenêtre de **Propriétés** , cliquez sur le champ de valeur de **Chemin d'accès de la propriété**.  sélectionnez **Commentaire**, puis **CommentReferencesSubject**, puis **élément de flux**.  Le chemin d'accès en résulte doit ressembler à **CommentReferencesSubject.Subject\/\!Objet**.  
  
7.  Dans le champ valeur de **Property**, sélectionnez **Nom**.  
  
8.  Transformez tous les modèles, puis générez et exécutez votre solution.  
  
9. Dans le concepteur généré, ouvrez le diagramme d'exemple.  
  
10. Dessinez **connecteur de commentaire** entre l'élément commentaire et l'élément de **Tâche1** sur le diagramme.  
  
     Le nœud de l'explorateur doit afficher le commentaire comme **Tâche1**.  
  
## Masquer les nœuds  
 Vous pouvez masquer un nœud dans votre explorateur en ajoutant son chemin d'accès au nœud de **Nœuds masqués** d' **Explorateur DÉSOLÉ**.  La procédure suivante explique comment masquer les nœuds de commentaire.  
  
#### Pour masquer un nœud de l'explorateur  
  
1.  Ouvrez la solution que vous avez créée dans la procédure antérieure.  
  
2.  Dans **Explorateur DÉSOLÉ**, cliquez avec le bouton droit sur **Comportement de l'explorateur** puis cliquez sur **ajoutez le nouveau chemin d'accès de domaine**.  
  
     Un nœud de **chemin d'accès de domaine** apparaît sous **Nœuds masqués**.  
  
3.  Sélectionnez **chemin d'accès de domaine**, puis dans la fenêtre de **Propriétés** , cliquez sur le champ de valeur de **définition de chemin d'accès**.  sélectionnez **organigramme**, puis **FlowGraphHasComments**.  Le chemin d'accès en résulte doit ressembler à **FlowGraphHasComments.Comments**  
  
4.  Transformez tous les modèles, puis générez et exécutez votre solution.  
  
5.  Dans le concepteur généré, ouvrez le diagramme d'exemple.  
  
     L'explorateur doit afficher uniquement un nœud d' **Acteurs** , et ne doit pas afficher le nœud de **Comments** .  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)