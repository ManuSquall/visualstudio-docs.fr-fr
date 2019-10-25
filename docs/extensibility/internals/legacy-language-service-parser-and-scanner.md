---
title: Analyseur et analyseur de service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726736"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanneur et analyseur du service de langage hérité
L’analyseur est le cœur du service de langage. Les classes de langages MPF (Managed package Framework) requièrent un analyseur de langage pour sélectionner des informations sur le code affiché. Un analyseur sépare le texte en jetons lexicals, puis identifie ces jetons par type et par fonctionnalité.

## <a name="discussion"></a>Discussion
 L’exemple suivant est C# une méthode.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 Dans cet exemple, les jetons sont les mots et les signes de ponctuation. Les types de jetons sont les suivants.

|Nom du jeton|Type de jeton|
|----------------|----------------|
|Namespace, Class, public, void, int|keyword|
|=|operator|
|{ } ( ) ;|limite|
|MyNamespace, MyClass, MyFunction, Arg1, var1|'identificateur'|
|MyNamespace|namespace|
|Classe|classe|
|MyFunction|méthode|
|Arg1|paramètre|
|var1|Variable locale|

 Le rôle de l’analyseur est d’identifier les jetons. Certains jetons peuvent avoir plusieurs types. Une fois que l’analyseur a identifié les jetons, le service de langage peut utiliser ces informations pour fournir des fonctionnalités utiles, telles que la mise en surbrillance de la syntaxe, la correspondance des accolades et les opérations IntelliSense.

## <a name="types-of-parsers"></a>Types d’analyseurs
 Un analyseur de service de langage n’est pas identique à un analyseur utilisé dans le cadre d’un compilateur. Toutefois, ce type d’analyseur doit utiliser à la fois un scanneur et un analyseur, de la même façon qu’un analyseur de compilateur.

- Un scanneur est utilisé pour identifier les types de jetons. Ces informations sont utilisées pour la mise en surbrillance de la syntaxe et pour identifier rapidement les types de jetons qui peuvent déclencher d’autres opérations, par exemple, la correspondance des accolades. Ce scanneur est représenté par l’interface <xref:Microsoft.VisualStudio.Package.IScanner>.

- Un analyseur est utilisé pour décrire les fonctions et l’étendue des jetons. Ces informations sont utilisées dans les opérations IntelliSense pour identifier les éléments de langage, tels que les méthodes, les variables, les paramètres et les déclarations, et pour fournir des listes de membres et des signatures de méthode basées sur le contexte. Cet analyseur est également utilisé pour localiser les paires d’éléments de langage correspondantes, telles que les accolades et les parenthèses. Cet analyseur est accessible par le biais de la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> de la classe <xref:Microsoft.VisualStudio.Package.LanguageService>.

  La façon dont vous implémentez un scanneur et un analyseur pour votre service de langage dépend de vous. Plusieurs ressources sont disponibles qui décrivent le fonctionnement des analyseurs et comment écrire votre propre analyseur. En outre, plusieurs produits gratuits et commerciaux sont disponibles pour vous aider à créer un analyseur.

### <a name="the-parsesource-parser"></a>Analyseur ParseSource
 Contrairement à un analyseur utilisé dans le cadre d’un compilateur (où les jetons sont convertis en une forme de code exécutable), un analyseur de service de langage peut être appelé pour de nombreuses raisons différentes et dans de nombreux contextes différents. La façon dont vous implémentez cette approche dans la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> de la classe <xref:Microsoft.VisualStudio.Package.LanguageService> dépend de vous. Il est important de garder à l’esprit que la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> peut être appelée sur un thread d’arrière-plan.

> [!CAUTION]
> La structure <xref:Microsoft.VisualStudio.Package.ParseRequest> contient une référence à l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Cet objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ne peut pas être utilisé dans le thread d’arrière-plan. En fait, la plupart des classes de base MPF ne peuvent pas être utilisées dans le thread d’arrière-plan. Celles-ci incluent les classes <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> et toute autre classe qui communique directement ou indirectement avec la vue.

 Cet analyseur analyse généralement l’intégralité du fichier source la première fois qu’il est appelé ou lorsque la valeur de la raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> est donnée. Les appels suivants à la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> gèrent une petite partie du code analysé et peuvent être exécutés plus rapidement en utilisant les résultats de l’opération d’analyse complète précédente. La méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> communique les résultats de l’opération d’analyse par le biais des objets <xref:Microsoft.VisualStudio.Package.AuthoringSink> et <xref:Microsoft.VisualStudio.Package.AuthoringScope>. L’objet <xref:Microsoft.VisualStudio.Package.AuthoringSink> est utilisé pour collecter des informations pour une raison d’analyse spécifique, par exemple, des informations sur les étendues d’accolades correspondantes ou les signatures de méthode qui ont des listes de paramètres. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> fournit des collections de signatures et des signatures de méthode, et prend également en charge l’option Go to Advanced Edit (**atteindre la définition**, **atteindre la déclaration**, atteindre la **référence**).

### <a name="the-iscanner-scanner"></a>Le scanneur IScanner
 Vous devez également implémenter un scanneur qui implémente <xref:Microsoft.VisualStudio.Package.IScanner>. Toutefois, étant donné que ce scanneur s’exécute ligne par ligne via la classe <xref:Microsoft.VisualStudio.Package.Colorizer>, il est généralement plus facile à implémenter. Au début de chaque ligne, le MPF donne à la classe <xref:Microsoft.VisualStudio.Package.Colorizer> une valeur à utiliser comme variable d’État qui est transmise au scanneur. À la fin de chaque ligne, le scanneur retourne la variable d’État mise à jour. Le MPF met en cache ces informations d’État pour chaque ligne afin que le scanneur puisse commencer l’analyse à partir de n’importe quelle ligne sans avoir à démarrer au début du fichier source. Cette analyse rapide d’une seule ligne permet à l’éditeur de fournir des commentaires rapides à l’utilisateur.

## <a name="parsing-for-matching-braces"></a>Analyse pour les accolades correspondantes
 Cet exemple montre le déroulement du contrôle pour la correspondance d’une accolade fermante que l’utilisateur a tapée. Dans ce processus, le scanneur utilisé pour la colorisation est également utilisé pour déterminer le type de jeton et si le jeton peut déclencher une opération de correspondance des accolades. Si le déclencheur est trouvé, la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> est appelée pour Rechercher l’accolade correspondante. Enfin, les deux accolades sont mises en surbrillance.

 Bien que les accolades soient utilisées dans les noms des déclencheurs et les raisons de l’analyse, ce processus n’est pas limité aux accolades réelles. Toute paire de caractères spécifiée comme étant une paire correspondante est prise en charge. Exemples : (et), \< et >, et [et].

 Supposons que le service de langage prend en charge les accolades correspondantes.

1. L’utilisateur tape une accolade fermante (}).

2. L’accolade est insérée au niveau du curseur dans le fichier source et le curseur est avancé d’une unité.

3. La méthode <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> de la classe <xref:Microsoft.VisualStudio.Package.Source> est appelée avec l’accolade fermante typée.

4. La méthode <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> appelle la méthode <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> dans la classe <xref:Microsoft.VisualStudio.Package.Source> pour obtenir le jeton à la position juste avant la position actuelle du curseur. Ce jeton correspond à l’accolade fermante typée.

    1. La méthode <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> appelle la méthode <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> sur l’objet <xref:Microsoft.VisualStudio.Package.Colorizer> pour obtenir tous les jetons sur la ligne actuelle.

    2. La méthode <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> appelle la méthode <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> sur l’objet <xref:Microsoft.VisualStudio.Package.IScanner> avec le texte de la ligne active.

    3. La méthode <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> appelle à plusieurs reprises la méthode <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> sur l’objet <xref:Microsoft.VisualStudio.Package.IScanner> pour rassembler tous les jetons de la ligne active.

    4. La méthode <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> appelle une méthode privée dans la classe <xref:Microsoft.VisualStudio.Package.Source> pour obtenir le jeton qui contient la position souhaitée et transmet la liste des jetons obtenus à partir de la méthode <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>.

5. La méthode <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> recherche un indicateur de déclencheur de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton retourné par la méthode <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> ; autrement dit, le jeton qui représente l’accolade fermante).

6. Si l’indicateur de déclencheur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> est trouvé, la méthode <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> dans la classe <xref:Microsoft.VisualStudio.Package.Source> est appelée.

7. La méthode <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> démarre une opération d’analyse avec la valeur de raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Cette opération appelle finalement la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sur la classe <xref:Microsoft.VisualStudio.Package.LanguageService>. Si l’analyse asynchrone est activée, cet appel à la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> se produit sur un thread d’arrière-plan.

8. Lorsque l’opération d’analyse est terminée, un gestionnaire d’achèvement interne (également appelé méthode de rappel) nommé `HandleMatchBracesResponse` est appelé dans la classe <xref:Microsoft.VisualStudio.Package.Source>. Cet appel est effectué automatiquement par la classe de base <xref:Microsoft.VisualStudio.Package.LanguageService>, et non par l’analyseur.

9. La méthode `HandleMatchBracesResponse` obtient une liste d’étendues à partir de l’objet <xref:Microsoft.VisualStudio.Package.AuthoringSink> stocké dans l’objet <xref:Microsoft.VisualStudio.Package.ParseRequest>. (Une étendue est une structure <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> qui spécifie une plage de lignes et de caractères dans le fichier source.) Cette liste d’étendues contient généralement deux étendues, une pour les accolades ouvrantes et fermantes.

10. La méthode `HandleBracesResponse` appelle la méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> sur l’objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> qui est stocké dans l’objet <xref:Microsoft.VisualStudio.Package.ParseRequest>. Cela met en évidence les étendues données.

11. Si la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> est activée, la méthode `HandleBracesResponse` obtient le texte qui est englobé par l’étendue correspondante et affiche les 80 premiers caractères de cette étendue dans la barre d’État. Cela fonctionne mieux si la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> comprend l’élément de langage qui accompagne la paire correspondante. Pour plus d'informations, consultez la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Cas.

### <a name="summary"></a>Récapitulatif
 L’opération d’accolades correspondante est généralement limitée à des paires simples d’éléments de langage. Les éléments plus complexes, tels que les triplets (« `if(...)` », « `{` » et « `}` », ou « `else` », « `{` » et « `}` »), peuvent être mis en surbrillance dans le cadre d’une opération de saisie semi-automatique. Par exemple, lorsque le mot « else » est terminé, l’instruction « `if` » correspondante peut être mise en surbrillance. S’il existe une série de `if` / des instructions `else if`, elles peuvent toutes être mises en surbrillance à l’aide du même mécanisme que les accolades correspondantes. La classe de base <xref:Microsoft.VisualStudio.Package.Source> prend déjà en charge ce qui suit : le scanneur doit retourner la valeur du déclencheur de jeton <xref:Microsoft.VisualStudio.Package.TokenTriggers> associée à la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour le jeton qui précède la position du curseur.

 Pour plus d’informations, consultez [correspondance des accolades dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analyse de la colorisation
 La coloration du code source est simple, il vous suffit d’identifier le type de jeton et de retourner des informations de couleur sur ce type. La classe <xref:Microsoft.VisualStudio.Package.Colorizer> agit comme intermédiaire entre l’éditeur et le scanneur pour fournir des informations de couleur sur chaque jeton. La classe <xref:Microsoft.VisualStudio.Package.Colorizer> utilise l’objet <xref:Microsoft.VisualStudio.Package.IScanner> pour aider à colorier une ligne et à collecter des informations d’État pour toutes les lignes du fichier source. Dans les classes du service de langage MPF, la classe <xref:Microsoft.VisualStudio.Package.Colorizer> ne doit pas être remplacée car elle communique avec le scanneur uniquement via l’interface <xref:Microsoft.VisualStudio.Package.IScanner>. Vous fournissez l’objet qui implémente l’interface <xref:Microsoft.VisualStudio.Package.IScanner> en substituant la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> sur la classe <xref:Microsoft.VisualStudio.Package.LanguageService>.

 Le scanneur <xref:Microsoft.VisualStudio.Package.IScanner> reçoit une ligne de code source via la méthode <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>. Les appels à la méthode <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> sont répétés pour obtenir le jeton suivant dans la ligne jusqu’à épuisement des jetons de la ligne. Pour la colorisation, le MPF traite tout le code source comme une séquence de lignes. Par conséquent, le scanneur doit être en mesure de faire face à la source en ligne. En outre, toute ligne peut être transmise au scanneur à tout moment, et la seule garantie est que le moteur d’analyse reçoit la variable d’État à partir de la ligne avant la ligne à analyser.

 La classe <xref:Microsoft.VisualStudio.Package.Colorizer> est également utilisée pour identifier les déclencheurs de jeton. Ces déclencheurs indiquent au MPF qu’un jeton particulier peut lancer une opération plus complexe, telle que la saisie de mots ou des accolades correspondantes. Étant donné que l’identification de ces déclencheurs doit être rapide et doit se produire à n’importe quel emplacement, le scanneur est mieux adapté à cette tâche.

 Pour plus d’informations, consultez [colorisation de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analyse des fonctionnalités et de la portée
 L’analyse des fonctionnalités et de l’étendue nécessite plus d’efforts que d’identifier simplement les types de jetons rencontrés. L’analyseur doit identifier non seulement le type de jeton, mais également la fonctionnalité pour laquelle le jeton est utilisé. Par exemple, un identificateur est simplement un nom, mais dans votre langage, un identificateur peut être le nom d’une classe, d’un espace de noms, d’une méthode ou d’une variable, selon le contexte. Le type général du jeton peut être un identificateur, mais l’identificateur peut également avoir d’autres significations, en fonction de ce qu’il est et de l’emplacement où il est défini. Cette identification oblige l’analyseur à avoir des connaissances plus étendues sur la langue en cours d’analyse. C’est là qu’intervient la classe <xref:Microsoft.VisualStudio.Package.AuthoringSink>. La classe <xref:Microsoft.VisualStudio.Package.AuthoringSink> collecte des informations sur les identificateurs, les méthodes, les paires de langages correspondantes (telles que les accolades et les parenthèses) et les triplets de langue (similaires aux paires de langage, sauf qu’il existe trois parties, par exemple, « `foreach()` » « `{` » et « `}` ») . En outre, vous pouvez substituer la classe <xref:Microsoft.VisualStudio.Package.AuthoringSink> pour prendre en charge l’identification de code, qui est utilisée lors de la validation précoce des points d’arrêt afin que le débogueur n’ait pas besoin d’être chargé, et la fenêtre de débogage **automatique** , qui affiche les variables locales et les paramètres. automatiquement lorsqu’un programme est en cours de débogage et nécessite que l’analyseur identifie les variables locales et les paramètres appropriés en plus de ceux que le débogueur présente.

 L’objet <xref:Microsoft.VisualStudio.Package.AuthoringSink> est passé à l’analyseur dans le cadre de l’objet <xref:Microsoft.VisualStudio.Package.ParseRequest>, et un nouvel objet <xref:Microsoft.VisualStudio.Package.AuthoringSink> est créé chaque fois qu’un nouvel objet <xref:Microsoft.VisualStudio.Package.ParseRequest> est créé. En outre, la méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> doit retourner un objet <xref:Microsoft.VisualStudio.Package.AuthoringScope>, qui est utilisé pour gérer différentes opérations IntelliSense. L’objet <xref:Microsoft.VisualStudio.Package.AuthoringScope> gère une liste pour les déclarations et une liste pour les méthodes, chacune d’elles étant remplie, en fonction de la raison de l’analyse. La classe <xref:Microsoft.VisualStudio.Package.AuthoringScope> doit être implémentée.

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)