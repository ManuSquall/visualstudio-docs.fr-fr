---
title: "How to: Create a Nullable Type (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nullable types, Class Designer"
  - "Class Designer [Visual Studio], nullable types"
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create a Nullable Type (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Certains types valeur ne disposent pas toujours \(ou n'ont pas toujours besoin\) d'une valeur définie.  Cela est courant dans les bases de données, où certains champs n'ont parfois aucune valeur assignée.  Par exemple, vous pouvez assigner une valeur Null à un champ de base de données pour indiquer qu'aucune valeur ne lui a encore été assignée.  
  
 Un *type Nullable* est un type valeur que vous étendez afin qu'il prenne la plage des valeurs de ce type ainsi qu'une valeur Null.  Par exemple, un type Nullable `Int32` \(Nullable\<Int32\>\), peut avoir une valeur comprise entre \-2147483648 et 2147483647, ou une valeur Null.  Un Nullable \<bool\> peut se voir assigner les valeurs `True`, `False` ou null \(aucune valeur\).  
  
 Les types Nullable sont des instances de la structure <xref:System.Nullable%601>.  Chaque instance de type Nullable a deux propriétés publiques en lecture seule, `HasValue` et `Value` :  
  
-   `HasValue` est de type `bool` et indique si la variable contient une valeur définie.  `True` signifie que la variable contient une valeur non null.  Vous pouvez tester une valeur définie à l'aide d'une instruction telle que `if (x.HasValue)` ou `if (y != null)`.  
  
-   `Value` est du même type que le type sous\-jacent.  Si `HasValue` a la valeur `True`, `Value` contient une valeur significative.  Si `HasValue` est `False`, l'accès à `Value` lèvera une exception d'opération incorrecte.  
  
 Par défaut, lorsque vous déclarez une variable en tant que type Nullable, aucune valeur n'est définie \(`HasValue` est `False`\), à part la valeur par défaut de son type valeur sous\-jacent.  
  
 Le concepteur de classes affiche un type Nullable comme il affiche son type sous\-jacent.  
  
 Pour plus d'informations sur les types qui autorisent la valeur Null en Visual C\#, consultez [Types Nullable](/dotnet/csharp/programming-guide/nullable-types/index).  Pour plus d'informations sur les types qui autorisent la valeur Null en Visual Basic, consultez [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour ajouter un type Nullable à l'aide du concepteur de classes  
  
1.  Dans le diagramme de classes, développez une classe existante ou créez une nouvelle classe.  
  
2.  Pour ajouter une classe au projet, cliquez sur **Ajouter** dans le menu **Diagramme de classes**, puis cliquez sur **Ajouter une classe**.  
  
3.  Pour développer la forme de classe, dans le menu **Diagramme de classes**, cliquez sur **Développer**.  
  
4.  Sélectionnez la forme de classe.  Dans le menu **Diagramme de classes**, cliquez sur **Ajouter**, puis sur **Champ**.  Un nouveau champ avec le nom par défaut **Champ** apparaît dans la forme de classe et dans la fenêtre **Détails de classe**.  
  
5.  Dans la colonne **Nom** de la fenêtre **Détails de classe** \(ou dans la forme de classe elle\-même\), remplacez le nom du nouveau champ par un nom valide et explicite.  
  
6.  Dans la colonne **Type** de la fenêtre **Détails de classe**, déclarez le type en tant que type Nullable, comme indiqué dans le code suivant :  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
### Pour ajouter un type Nullable en utilisant l'Éditeur de code  
  
1.  Ajoutez une classe au projet.  Sélectionnez le nœud de projet dans l'**Explorateur de solutions** puis, dans le menu **Projet**, cliquez sur **Ajouter une classe**.  
  
2.  Dans le fichier .cs ou .vb pour la nouvelle classe, ajoutez un ou plusieurs types Nullable de la nouvelle classe à la déclaration de classe.  
  
3.  Dans l'affichage de classes, faites glisser l'icône de la nouvelle classe vers l'aire de conception du concepteur de classes.  Une forme de classe apparaît dans le diagramme de classes.  
  
4.  Développez les détails pour la forme de classe et déplacez le pointeur de la souris sur les membres de la classe.  L'info\-bulle affiche la déclaration de chaque membre.  
  
5.  Cliquez avec le bouton droit sur la forme de classe, puis cliquez sur **Détails de classe**.  Vous pouvez afficher ou modifier les propriétés du nouveau type dans la fenêtre **Détails de classe**.  
  
## Voir aussi  
 <xref:System.Nullable%601>   
 [Types Nullable](/dotnet/csharp/programming-guide/nullable-types/index)   
 [Utilisation de types Nullable](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)   
 [Comment : identifier un type Nullable](../Topic/How%20to:%20Identify%20a%20Nullable%20Type%20\(C%23%20Programming%20Guide\).md)   
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)