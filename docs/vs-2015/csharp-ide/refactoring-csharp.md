---
title: Refactorisation (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667499"
---
# <a name="refactoring-c"></a>Refactorisation (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La refactorisation est le processus qui consiste à améliorer votre code une fois qu’il a été écrit en modifiant la structure interne du code sans modifier le comportement externe du code.

 L' C# élément visuel fournit les commandes de refactorisation suivantes dans le menu **refactorisation** :

- [Extraire la méthode (Refactorisation C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Refactorisation de changement de nom (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Encapsuler le champ (Refactorisation C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Refactorisation d’extraction d’interface (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Supprimer les paramètres (Refactorisation C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Réorganiser les paramètres (opération de refactorisation C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refactorisation de plusieurs projets
 Visual Studio prend en charge la refactorisation de plusieurs projets pour les projets qui se trouvent dans la même solution. Toutes les opérations de refactorisation qui corrigent les références dans les fichiers corrigent ces références dans tous les projets de la même langue. Cela fonctionne pour toutes les références entre projets. Par exemple, si vous avez une application console qui fait référence à une bibliothèque de classes, lorsque vous renommez un type de bibliothèque de classes (à l’aide de l’opération de refactorisation `Rename`), les références au type de bibliothèque de classes dans l’application console sont également mises à jour.

## <a name="changes-preview"></a>Aperçu des modifications
 De nombreuses opérations de refactorisation vous donnent la possibilité d’examiner toutes les modifications de référence qu’une opération de refactorisation effectuerait sur votre code, avant de valider ces modifications. Pour ces opérations de refactorisation, une option **aperçu des modifications** de la référence s’affiche dans la boîte de dialogue refactorisation. Une fois cette option sélectionnée et en acceptant l’opération de refactorisation, la **boîte de dialogue Aperçu des modifications** s’affiche. Notez que la boîte de dialogue **aperçu des modifications** comporte deux vues. La vue inférieure affiche votre code avec toutes les mises à jour de référence en raison de l’opération de refactorisation. Si vous appuyez sur **Annuler** dans la boîte de dialogue **aperçu des modifications** , l’opération de refactorisation est arrêtée et aucune modification n’est apportée à votre code.

## <a name="refactoring-warnings"></a>Avertissements de refactorisation
 Si le compilateur ne dispose pas d’une compréhension complète de votre programme et qu’il est possible que le moteur de refactorisation ne met pas à jour toutes les références appropriées, la boîte de dialogue d’avertissement s’affiche. Cette boîte de dialogue d’avertissement vous donne également la possibilité d’afficher un aperçu de votre code dans la boîte de dialogue **aperçu des modifications** avant de valider les modifications.

> [!NOTE]
> Si une méthode contient une erreur de syntaxe (que l’IDE signale avec un trait de soulignement ondulé rouge), le moteur de refactorisation ne met pas à jour les références à un élément de cette méthode. L’exemple ci-dessous illustre ce comportement.

 Par défaut, si vous exécutez une opération de refactorisation sans prévisualiser les modifications de référence et qu’une erreur de compilation est détectée dans votre programme, l’environnement de développement affiche cette boîte de dialogue d’avertissement.

 Si vous exécutez une opération de refactorisation pour laquelle l’option **aperçu des modifications** de la référence est activée et qu’une erreur de compilation est détectée dans votre programme, l’environnement de développement affichera le message d’avertissement suivant en bas de l' **aperçu des modifications.** au lieu d’afficher la boîte de dialogue d' **avertissement de refactorisation** :

 **Votre projet ou l’une de ses dépendances n’est pas actuellement généré. Les références ne peuvent pas être mises à jour.**

 Cet avertissement de refactorisation est disponible uniquement pour les opérations de refactorisation qui fournissent l’option **aperçu des modifications** de la référence.

## <a name="error-tolerant-refactoring-and-verification-results"></a>Résultats de la vérification et de la refactorisation tolérante aux erreurs
 La refactorisation est tolérante aux erreurs. En d’autres termes, vous pouvez effectuer une refactorisation dans un projet qui ne peut pas être généré. Toutefois, dans ce cas, le processus de refactorisation peut ne pas mettre à jour correctement les références ambiguës.

 La boîte de dialogue résultats de la **vérification** peut vous avertir si le moteur de refactorisation détecte des erreurs de compilation ou découvre qu’une opération de refactorisation provoque par inadvertance qu’une référence de code se lie à un autre élément que celui à partir duquel elle a été initialement liée ( problème de reliaison).

 Pour activer la fonctionnalité résultats de la vérification, dans le menu **Outils** , cliquez sur **options**. Dans la boîte de dialogue **options** , développez **éditeur de texte**, **C#** puis développez. Cliquez sur **avancé** , puis activez la case à cocher **vérifier les résultats de la refactorisation** .

 La boîte de dialogue résultats de la **vérification** distingue la différence entre deux genres de problèmes de reliaison.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Références dont la définition ne sera plus le symbole renommé
 Ce type de problème de reliaison se produit lorsqu’une référence ne fait plus référence à un symbole renommé. Considérons par exemple le code suivant :

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

 Si vous utilisez la refactorisation pour renommer `a` en `b`, cette boîte de dialogue s’affiche. La référence à la variable renommée `a` est désormais liée au paramètre passé au constructeur au lieu de se lier au champ.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Références dont la définition deviendra le symbole renommé
 Ce type de problème de reliaison se produit lorsqu’une référence qui ne faisait pas précédemment référence au symbole renommé fait désormais référence au symbole renommé. Considérons par exemple le code suivant :

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

 Si vous utilisez la refactorisation pour renommer `OtherMethod` en `Method`, cette boîte de dialogue s’affiche. La référence dans `Main` fait maintenant référence à la méthode surchargée qui accepte un paramètre `int` au lieu de la méthode surchargée qui accepte un paramètre `object`.

## <a name="see-also"></a>Voir aussi
 [Utilisation de l’environnement de développement Visual C# Studio pour](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [Comment : C# restaurer les extraits de code de refactorisation](../ide/how-to-restore-csharp-refactoring-snippets.md)