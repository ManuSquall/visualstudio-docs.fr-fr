---
title: 'Procédure : Créer un Type Nullable (Concepteur de classes) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d5e74a4384cff0a68764ffe09a37ab28460d58b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422809"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Procédure : Créer un type Nullable (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Certains types valeur n’ont pas, ou n’ont pas besoin d’avoir, systématiquement une valeur définie. Il s’agit d’une pratique courante dans les bases de données, où certains champs peuvent ne se voir assigner aucune valeur. Par exemple, vous pouvez assigner une valeur null à un champ de base de données, qu’il conservera jusqu’à ce qu’une valeur lui soit affectée.  
  
 Un *type Nullable* est un type de valeur que vous étendez afin qu’il accepte la plage ordinaire de valeurs de ce type, ainsi qu’une valeur null. Par exemple, un type Nullable `Int32`, également appelé Nullable\<Int32>, peut se voir assigner n’importe quelle valeur entre -2147483648 et 2147483647, ou une valeur null. Un type Nullable\<bool> peut se voir assigner les valeurs `True`, `False` ou null (aucune valeur).  
  
 Les types Nullable sont des instances de la structure <xref:System.Nullable%601>. Chaque instance d’un type Nullable a deux propriétés publiques en lecture seule, `HasValue` et `Value` :  
  
- `HasValue` est de type `bool` et indique si la variable contient une valeur définie. `True` signifie que la variable contient une valeur non null. Vous pouvez tester l’existence d’une valeur définie en utilisant une instruction telle que `if (x.HasValue)` ou `if (y != null)`.  
  
- `Value` est du même type que le type sous-jacent. Si `HasValue` est `True`, `Value` contient une valeur significative. Si `HasValue` est `False`, l’accès à `Value` lève une exception d’opération non valide.  
  
  Par défaut, quand vous déclarez une variable en tant que type Nullable, elle n’a aucune valeur définie (`HasValue` est `False`), autre que la valeur par défaut de son type valeur sous-jacent.  
  
  Le Concepteur de classes affiche un type Nullable à l’image de son type sous-jacent.  
  
  Pour plus d’informations sur les types Nullable dans Visual C#, consultez [Types Nullable](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Pour plus d’informations sur les types Nullable dans Visual Basic, consultez [Types valeur Nullable](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Pour ajouter un type Nullable à l’aide du Concepteur de classes  
  
1. Dans le diagramme de classes, développez une classe existante ou créez une classe.  
  
2. Pour ajouter une classe au projet, dans le menu **Diagramme de classes**, cliquez sur **Ajouter**, puis cliquez sur **Ajouter une classe**.  
  
3. Pour développer la forme de classe, dans le menu **Diagramme de classes**, cliquez sur **Développer**.  
  
4. Sélectionnez la forme de classe. Dans le menu **Diagramme de classes**, cliquez sur **Ajouter**, puis cliquez sur **Champ**. Un nouveau champ qui porte le nom par défaut **Champ** apparaît dans la forme de classe, ainsi que dans la fenêtre **Détails de classe**.  
  
5. Dans la colonne **Nom** de la fenêtre **Détails de classe** (ou dans la classe de forme elle-même), remplacez le nom du nouveau champ par un nom valide et explicite.  
  
6. Dans la colonne **Type** de la fenêtre **Détails de classe**, déclarez le type en tant que type Nullable, comme indiqué dans le code suivant :  
  
    ```csharp  
    // Declare a nullable type in Visual C#:  
    class Test  
    {  
       int? building_number = 5;  
    }  
    ```  
  
    ```vb  
    ' Declare a nullable type in Visual Basic:  
    Class Test  
       Dim buildingNumber As Nullable(Of Integer) = 5  
    End Class  
    ```  
  
### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Pour ajouter un type Nullable à l’aide de l’éditeur de code  
  
1. Ajoutez une classe au projet. Sélectionnez le nœud du projet dans l’**Explorateur de solutions**, puis, dans le menu **Projet**, cliquez sur **Ajouter une classe**.  
  
2. Dans le fichier .cs ou .vb pour la nouvelle classe, ajoutez un ou plusieurs types Nullable dans la nouvelle classe à la déclaration de classe.  
  
3. À partir de l’affichage de classes, faites glisser l’icône de la nouvelle classe vers l’aire de conception du Concepteur de classes. Une forme de classe apparaît dans le diagramme de classes.  
  
4. Développez les détails de la forme de classe et déplacez le pointeur de la souris sur les membres de classe. L’info-bulle affiche la déclaration de chaque membre.  
  
5. Cliquez avec le bouton droit sur la forme de classe, puis cliquez sur **Détails de classe**. Vous pouvez afficher ou modifier les propriétés du nouveau type dans la fenêtre **Détails de classe**.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Nullable%601>   
 [Types Nullable](http://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)   
 [Utilisation de types Nullable](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)   
 [Guide pratique pour Identifier un Type Nullable](http://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387)   
 [Types valeur Nullable](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)
