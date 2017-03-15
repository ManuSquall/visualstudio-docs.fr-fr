---
title: "Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.preview"
  - "vs.csharp.refactoring.issues"
  - "vs.csharp.refactoring.buildwarning"
  - "VS.PreviewChanges"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#]"
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La refactorisation est le processus qui consiste à améliorer votre code après qu'il ait été écrit en modifiant sa structure interne sans modifier le comportement extérieur du code.  
  
 Visual C\# fournit les commandes de refactorisation suivantes dans le menu **Refactorisation** :  
  
-   [Extraire la méthode \(Refactorisation C\#\)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refactorisation de changement de nom \(C\#\)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsulate Field Refactoring \(C\#\)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Extract Interface Refactoring \(C\#\)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Supprimer les paramètres \(Refactorisation C\#\)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Reorder Parameters Refactoring \(C\#\)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## Refactorisation multi\-projet  
 Visual Studio prend en charge la refactorisation multi\-projet pour les projets qui se trouvent dans la même solution.  Toutes les opérations de refactorisation qui visent à corriger des références entre fichiers corrigent ces références dans tous les projets du même langage.  Ceci fonctionne pour toutes les références entre projets.  Par exemple, si vous avez une application console qui référence une bibliothèque de classes, lorsque vous renommez un type de bibliothèque de classes \(à l'aide de l'opération de refactorisation `Rename`\), les références au type de bibliothèque de classes tapent sont également mises à jour dans l'application console.  
  
## Aperçu des modifications  
 De nombreuses opérations de refactorisation vous permettent d'examiner toutes les modifications de référence qu'une opération de refactorisation apporterait à votre code, avant de valider à ces modifications.  Pour ces opérations de refactorisation, une option **Afficher un aperçu des modifications de la référence** apparaîtra dans la boîte de dialogue de refactorisation.  Une fois que vous avez sélectionné cette option et accepté l'opération de refactorisation, la **boîte de dialogue Aperçu des modifications** s'affiche.  Remarquez que la boîte de dialogue **Aperçu des modifications** a deux affichages.  L'affichage inférieur affiche votre code avec toutes les mises à jour des références issues de l'opération de refactorisation.  Appuyer sur **Annuler** dans la boîte de dialogue **Aperçu des modifications** arrêtera l'opération de refactorisation, et aucune modification ne sera apportée à votre code.  
  
## Avertissement de refactorisation  
 Si le compilateur ne comprend pas parfaitement le fonctionnement de votre programme et que le moteur de refactorisation risque de ne pas mettre à jour toutes les références appropriées, la boîte de dialogue d'avertissement s'affiche.  Cette boîte de dialogue d'avertissement vous permet également de prévisualiser votre code dans la boîte de dialogue **Aperçu des modifications** avant de valider les modifications.  
  
> [!NOTE]
>  Si une méthode contient une erreur de syntaxe \(que l'IDE signale d'une ligne de soulignement ondulée rouge\), le moteur de refactorisation ne mettra pas à jour de références à un élément dans cette méthode.  L'exemple suivant illustre ce comportement :  
  
 Par défaut, si vous exécutez une opération de refactorisation sans afficher d'aperçu des modifications de référence et qu'une erreur de compilation est détectée dans votre programme, l'environnement de développement affiche cette boîte de dialogue d'avertissement.  
  
 Si vous exécutez une opération de refactorisation pour laquelle l'option **Afficher un aperçu des modifications de la référence** est activée et qu'une erreur de compilation est détectée dans votre programme, l'environnement de développement affiche le message d'avertissement suivant en bas de la boîte de dialogue **Aperçu des modifications**, au lieu d'afficher la boîte de dialogue **Avertissement de refactorisation** :  
  
 **Votre projet ou l'une de ses dépendances ne se génère pas actuellement.**  
 **Les références ne seront peut\-être pas mises à jour.**  
  
 Cet avertissement de refactorisation est disponible uniquement pour les opérations de refactorisation qui permettent d'utiliser l'option **Afficher un aperçu des modifications de la référence**.  
  
## Refactorisation à tolérance d'erreur et résultats de la vérification  
 La refactorisation tolère les erreurs.  En d'autres termes, vous pouvez effectuer une refactorisation dans un projet qui ne peut pas se générer.  Toutefois, dans ces situations, le processus de refactorisation peut ne pas réussir à mettre à jour les références ambiguës.  
  
 La boîte de dialogue **Résultats de la vérification** peut vous avertir si le moteur de refactorisation détecte des erreurs de compilation ou découvre qu'une opération de refactorisation relie par inadvertance une référence de code à un élément autre que celui auquel elle était initialement liée \(problème de reliaison\).  
  
 Pour activer la fonctionnalité des résultats de la vérification, dans le menu **Outils**, cliquez sur **Options**.  Dans la boîte de dialogue **Options**, développez **Éditeur de texte**, puis **C\#**.  Cliquez sur **Avancé** et activez la case à cocher **Vérifier les résultats de la refactorisation**.  
  
 La boîte de dialogue **Résultats de la vérification** distingue deux genres de problèmes de reliaison.  
  
### Références dont la définition ne sera plus le symbole renommé  
 Ce genre de problème de reliaison se produit lorsqu'une référence ne fait plus référence à un symbole renommé.  Considérons par exemple le code suivant :  
  
```c#  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Si vous utilisez la refactorisation pour renommer `a` en `b`, cette boîte de dialogue apparaît.  La référence à la variable renommée `a` est maintenant liée au paramètre qui est passé au constructeur au lieu d'être liée au champ.  
  
### Références dont la définition deviendra maintenant le symbole renommé  
 Ce genre de problème de reliaison se produit lorsqu'une référence qui ne faisait pas précédemment référence au symbole renommé fait maintenant référence au symbole renommé.  Considérons par exemple le code suivant :  
  
```c#  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Si vous utilisez la refactorisation pour renommer `OtherMethod` en `Method`, cette boîte de dialogue apparaît.  La référence dans `Main` fait maintenant référence à la méthode surchargée qui accepte un paramètre `int` plutôt qu'à la méthode surchargée qui accepte un paramètre `object`.  
  
## Voir aussi  
 [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Comment : restaurer les extraits de code de refactorisation C\#](../Topic/How%20to:%20Restore%20C%23%20Refactoring%20Snippets.md)