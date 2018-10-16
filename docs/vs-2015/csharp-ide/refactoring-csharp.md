---
title: Refactorisation (c#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4f74017a067d4681eb14ba4eb826df504497430
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262312"
---
# <a name="refactoring-c"></a>Refactorisation (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La refactorisation consiste à améliorer votre code après que qu’il a été écrit par la modification de la structure interne du code sans modifier le comportement du code externe.  
  
 Visual c# fournit les commandes de refactorisation suivantes sur le **Refactoring** menu :  
  
-   [Extraire la méthode (Refactorisation C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refactorisation de changement de nom (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Encapsuler le champ (Refactorisation C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Refactorisation d’extraction d’interface (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Supprimer les paramètres (Refactorisation C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Réorganiser les paramètres (opération de refactorisation C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Refactorisation de plusieurs projets  
 Visual Studio prend en charge la refactorisation de plusieurs projets pour les projets qui se trouvent dans la même solution. Toutes les opérations de refactorisation qui corriger des références entre fichiers corrigent ces références dans tous les projets de la même langue. Cela fonctionne pour toutes les références projet à projet. Par exemple, si vous disposez d’une application de console qui fait référence à une bibliothèque de classes, lorsque vous renommez un type de bibliothèque de classe (à l’aide de la `Rename` opération de refactorisation), les références au type de bibliothèque de classe dans l’application de console sont à jour également.  
  
## <a name="changes-preview"></a>Aperçu des modifications  
 De nombreuses opérations de refactorisation offrent une opportunité pour vous permettre d’examiner toutes les modifications de référence qu’une opération de refactorisation exécuterait sur votre code, avant de valider ces modifications. Pour ces opérations, de refactorisation un **afficher un aperçu des modifications de la référence** option s’affiche dans la boîte de dialogue de refactorisation. Après avoir sélectionné cette option et accepté l’opération de refactorisation, la **boîte de dialogue Aperçu modifications** s’affiche. Notez que le **aperçu des modifications** boîte de dialogue dispose de deux vues. L’affichage du bas affiche votre code avec toutes les mises à jour de référence en raison de l’opération de refactorisation. En appuyant sur **Annuler** sur le **aperçu des modifications** boîte de dialogue s’arrête l’opération de refactorisation, et aucune modification ne porteront sur votre code.  
  
## <a name="refactoring-warnings"></a>Avertissement de refactorisation  
 Si le compilateur n’a pas une compréhension complète de votre programme, et il est possible que le moteur de refactorisation ne peut pas mettre à jour la toutes les références appropriées, la boîte de dialogue d’avertissement s’affiche. Cette boîte de dialogue d’avertissement fournit également une opportunité pour vous permettre d’afficher un aperçu de votre code dans le **aperçu des modifications** boîte de dialogue avant de valider les modifications.  
  
> [!NOTE]
>  Si une méthode contient une erreur de syntaxe (indiquant l’IDE avec une ligne ondulée rouge), puis le moteur de refactorisation ne mettra pas à jour toutes les références à un élément au sein de cette méthode. L’exemple ci-dessous illustre ce comportement.  
  
 Par défaut, si vous exécutez une opération de refactorisation sans afficher un aperçu de référence modifie une erreur de compilation est détectée dans votre programme, puis l’environnement de développement affiche cette boîte de dialogue d’avertissement.  
  
 Si vous exécutez une opération de refactorisation a **aperçu des modifications de référence** est activé et une erreur de compilation est détectée dans votre programme, puis l’environnement de développement affiche le message d’avertissement suivant en bas de la **Aperçu des modifications** boîte de dialogue, au lieu d’afficher le **avertissement de refactorisation** boîte de dialogue :  
  
 **Votre projet ou l’une de ses dépendances ne génère pas actuellement. Références ne peuvent pas être mises à jour.**  
  
 Cet avertissement de refactorisation est disponible uniquement pour opérations de refactorisation qui fournissent le **aperçu des modifications de référence** option.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Refactorisation à tolérance d’erreur et les résultats de la vérification  
 La refactorisation est à tolérance d’erreur. En d’autres termes, vous pouvez effectuer une refactorisation dans un projet qui ne peut pas générer. Toutefois, dans ce cas le processus de refactorisation ne peut pas mettre à jour les références ambiguës correctement.  
  
 Le **résultats de la vérification** boîte de dialogue peut vous avertir si le moteur de refactorisation détecte des erreurs de compilation ou découvre qu’une opération de refactorisation relie par inadvertance une référence de code à lier à quelque chose de différent à partir de ce qu’il était lié à l’origine (problème de reliaison).  
  
 Pour activer les résultats de la vérification des fonctionnalités, sur le **outils** menu, cliquez sur **Options**. Dans le **Options** boîte de dialogue, développez **éditeur de texte**, puis développez **c#**. Cliquez sur **avancé** et sélectionnez le **vérifier les résultats de la refactorisation** case à cocher.  
  
 Le **résultats de la vérification** boîte de dialogue distingue deux types de problèmes de reliaison.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Références dont la définition ne sera plus le symbole renommé  
 Ce type de problème de reliaison se produit lorsqu’une référence ne fait plus référence à un symbole renommé. Considérons par exemple le code suivant :  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Si vous utilisez la refactorisation pour renommer `a` à `b`, cette boîte de dialogue s’affiche. La référence à la variable renommée `a` est maintenant liée au paramètre qui est passé au constructeur au lieu de la liaison au champ.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Références dont la définition deviendra le symbole renommé  
 Ce type de problème de reliaison se produit lorsqu’une référence qui auparavant ne fait pas référence au symbole renommé maintenant fait référence au symbole renommé. Considérons par exemple le code suivant :  
  
```csharp  
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
  
 Si vous utilisez la refactorisation pour renommer `OtherMethod` à `Method`, cette boîte de dialogue s’affiche. La référence dans `Main` maintenant fait référence à la méthode surchargée qui accepte un `int` paramètre au lieu de la méthode surchargée qui accepte un `object` paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’environnement de développement Visual Studio pour c#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Guide pratique pour restaurer les extraits de code de refactorisation C#](../ide/how-to-restore-csharp-refactoring-snippets.md)