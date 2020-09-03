---
title: Analyseur et analyseur de service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707312"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanneur et analyseur du service de langage hérité
L’analyseur est le cœur du service de langage. Les classes de langages MPF (Managed package Framework) requièrent un analyseur de langage pour sélectionner des informations sur le code affiché. Un analyseur sépare le texte en jetons lexicals, puis identifie ces jetons par type et par fonctionnalité.

## <a name="discussion"></a>Discussion
 Voici une méthode C#.

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

|Token Name (Nom du jeton)|Type de jeton|
|----------------|----------------|
|Namespace, Class, public, void, int|mot clé|
|=|operator|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, Arg1, var1|identificateur|
|MyNamespace|espace de noms|
|MyClass|class|
|MyFunction|method|
|arg1|paramètre|
|var1|variable locale|

 Le rôle de l’analyseur est d’identifier les jetons. Certains jetons peuvent avoir plusieurs types. Une fois que l’analyseur a identifié les jetons, le service de langage peut utiliser ces informations pour fournir des fonctionnalités utiles, telles que la mise en surbrillance de la syntaxe, la correspondance des accolades et les opérations IntelliSense.

## <a name="types-of-parsers"></a>Types d’analyseurs
 Un analyseur de service de langage n’est pas identique à un analyseur utilisé dans le cadre d’un compilateur. Toutefois, ce type d’analyseur doit utiliser à la fois un scanneur et un analyseur, de la même façon qu’un analyseur de compilateur.

- Un scanneur est utilisé pour identifier les types de jetons. Ces informations sont utilisées pour mettre en surbrillance la syntaxe et identifier rapidement les types de jetons qui peuvent déclencher d'autres opérations, par exemple des accolades correspondantes. Ce scanneur est représenté par l' <xref:Microsoft.VisualStudio.Package.IScanner> interface.

- Un analyseur est utilisé pour décrire les fonctions et l’étendue des jetons. Ces informations sont utilisées dans les opérations IntelliSense pour identifier les éléments de langage, tels que les méthodes, les variables, les paramètres et les déclarations, et pour fournir des listes de membres et des signatures de méthode basées sur le contexte. Cet analyseur est également utilisé pour localiser les paires d’éléments de langage correspondantes, telles que les accolades et les parenthèses. Cet analyseur est accessible par le biais <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> de la méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

  La façon dont vous implémentez un scanneur et un analyseur pour votre service de langage dépend de vous. Plusieurs ressources sont disponibles qui décrivent le fonctionnement des analyseurs et comment écrire votre propre analyseur. En outre, plusieurs produits gratuits et commerciaux sont disponibles pour vous aider à créer un analyseur.

### <a name="the-parsesource-parser"></a>Analyseur ParseSource
 Contrairement à un analyseur utilisé dans le cadre d’un compilateur (où les jetons sont convertis en une forme de code exécutable), un analyseur de service de langage peut être appelé pour de nombreuses raisons différentes et dans de nombreux contextes différents. La façon dont vous implémentez cette approche dans la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe dépend de vous. Il est important de garder à l’esprit que la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode peut être appelée sur un thread d’arrière-plan.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> structure contient une référence à l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet. Cet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet ne peut pas être utilisé dans le thread d’arrière-plan. En fait, la plupart des classes de base MPF ne peuvent pas être utilisées dans le thread d’arrière-plan. Celles-ci incluent les <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> classes,, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> et toute autre classe qui communique directement ou indirectement avec la vue.

 En général, cet analyseur analyse l’intégralité du fichier source la première fois qu’il est appelé ou lorsque la valeur de la raison de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> est donnée. Les appels suivants à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode gèrent une petite partie du code analysé et peuvent être exécutés plus rapidement en utilisant les résultats de l’opération d’analyse complète précédente. La <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode communique les résultats de l’opération d’analyse par le biais des <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> objets et. L' <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est utilisé pour collecter des informations pour une raison d’analyse spécifique, par exemple, des informations sur les étendues d’accolades correspondantes ou les signatures de méthode qui ont des listes de paramètres. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> fournit des collections de déclarations et de signatures de méthode, et prend également en charge l’option Go to Advanced Edit (**atteindre la définition**, **atteindre la déclaration**, atteindre la **référence**).

### <a name="the-iscanner-scanner"></a>Le scanneur IScanner
 Vous devez également implémenter un scanneur qui implémente <xref:Microsoft.VisualStudio.Package.IScanner> . Toutefois, étant donné que ce scanneur s’exécute ligne par ligne par le biais de la <xref:Microsoft.VisualStudio.Package.Colorizer> classe, il est généralement plus facile à implémenter. Au début de chaque ligne, le MPF donne à la <xref:Microsoft.VisualStudio.Package.Colorizer> classe une valeur à utiliser comme variable d’État qui est transmise au scanneur. À la fin de chaque ligne, le scanneur retourne la variable d’État mise à jour. Le MPF met en cache ces informations d’État pour chaque ligne afin que le scanneur puisse commencer l’analyse à partir de n’importe quelle ligne sans avoir à démarrer au début du fichier source. Cette analyse rapide d’une seule ligne permet à l’éditeur de fournir des commentaires rapides à l’utilisateur.

## <a name="parsing-for-matching-braces"></a>Analyse pour les accolades correspondantes
 Cet exemple montre le déroulement du contrôle pour la correspondance d’une accolade fermante que l’utilisateur a tapée. Dans ce processus, le scanneur utilisé pour la colorisation est également utilisé pour déterminer le type de jeton et si le jeton peut déclencher une opération de correspondance des accolades. Si le déclencheur est trouvé, la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est appelée pour Rechercher l’accolade correspondante. Enfin, les deux accolades sont mises en surbrillance.

 Bien que les accolades soient utilisées dans les noms des déclencheurs et les raisons de l’analyse, ce processus n’est pas limité aux accolades réelles. Toute paire de caractères spécifiée comme étant une paire correspondante est prise en charge. Exemples : (et), \< and > , et [et].

 Supposons que le service de langage prend en charge les accolades correspondantes.

1. L’utilisateur tape une accolade fermante (}).

2. L’accolade est insérée au niveau du curseur dans le fichier source et le curseur est avancé d’une unité.

3. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée avec l’accolade fermante typée.

4. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode appelle la <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton à la position juste avant la position actuelle du curseur. Ce jeton correspond à l’accolade fermante typée.

    1. La <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode appelle la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode sur l' <xref:Microsoft.VisualStudio.Package.Colorizer> objet pour obtenir tous les jetons sur la ligne actuelle.

    2. La <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode appelle la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> méthode sur l' <xref:Microsoft.VisualStudio.Package.IScanner> objet avec le texte de la ligne active.

    3. La <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode appelle à plusieurs reprises la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sur l' <xref:Microsoft.VisualStudio.Package.IScanner> objet pour rassembler tous les jetons de la ligne active.

    4. La <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode appelle une méthode privée dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton qui contient la position souhaitée et transmet la liste des jetons obtenus à partir de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode.

5. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode recherche un indicateur de déclencheur de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton retourné par la <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode, autrement dit, le jeton qui représente l’accolade fermante.

6. Si l’indicateur de déclencheur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> est trouvé, la <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée.

7. La <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode démarre une opération d’analyse avec la valeur de raison d’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason> . Cette opération appelle finalement la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Si l’analyse asynchrone est activée, cet appel à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode se produit sur un thread d’arrière-plan.

8. Lorsque l’opération d’analyse est terminée, un gestionnaire d’achèvement interne (également appelé méthode de rappel) nommé `HandleMatchBracesResponse` est appelé dans la <xref:Microsoft.VisualStudio.Package.Source> classe. Cet appel est effectué automatiquement par la <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base, et non par l’analyseur.

9. La `HandleMatchBracesResponse` méthode obtient une liste d’étendues à partir de l' <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet stocké dans l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. (Une étendue est une <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> structure qui spécifie une plage de lignes et de caractères dans le fichier source.) Cette liste d’étendues contient généralement deux étendues, une pour les accolades ouvrantes et fermantes.

10. La `HandleBracesResponse` méthode appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> méthode sur l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet qui est stocké dans l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. Cela met en évidence les étendues données.

11. Si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> est activée, la `HandleBracesResponse` méthode obtient le texte qui est englobé par l’étendue correspondante et affiche les 80 premiers caractères de cette étendue dans la barre d’État. Cela fonctionne mieux si la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode comprend l’élément de langage qui accompagne la paire correspondante. Pour plus d'informations, consultez la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Opération terminée.

### <a name="summary"></a>Résumé
 L’opération d’accolades correspondante est généralement limitée à des paires simples d’éléments de langage. Les éléments plus complexes, tels que les triplets (« `if(...)` », « `{` » et « », ou « », « » et « » `}` `else` `{` `}` ), peuvent être mis en surbrillance dans le cadre d’une opération de saisie semi-automatique. Par exemple, lorsque le mot « else » est terminé, l’instruction « `if` » correspondante peut être mise en surbrillance. S’il existe une série d' `if` / `else if` instructions, elles peuvent toutes être mises en surbrillance à l’aide du même mécanisme que les accolades correspondantes. La <xref:Microsoft.VisualStudio.Package.Source> classe de base prend déjà en charge cette fonction, comme suit : le scanneur doit retourner la valeur <xref:Microsoft.VisualStudio.Package.TokenTriggers> de déclenchement de jeton associée à la valeur de déclenchement du <xref:Microsoft.VisualStudio.Package.TokenTriggers> jeton qui précède la position du curseur.

 Pour plus d’informations, consultez [correspondance des accolades dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analyse de la colorisation
 La coloration du code source est simple, il vous suffit d’identifier le type de jeton et de retourner des informations de couleur sur ce type. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe agit comme intermédiaire entre l’éditeur et le scanneur pour fournir des informations de couleur sur chaque jeton. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilise l' <xref:Microsoft.VisualStudio.Package.IScanner> objet pour aider à coloriser une ligne et à collecter des informations d’État pour toutes les lignes dans le fichier source. Dans les classes du service de langage MPF, la <xref:Microsoft.VisualStudio.Package.Colorizer> classe n’a pas besoin d’être substituée, car elle communique avec le scanneur uniquement via l' <xref:Microsoft.VisualStudio.Package.IScanner> interface. Vous fournissez l’objet qui implémente l' <xref:Microsoft.VisualStudio.Package.IScanner> interface en substituant la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

 Le <xref:Microsoft.VisualStudio.Package.IScanner> scanneur reçoit une ligne de code source via la <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> méthode. Les appels à la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sont répétés pour obtenir le jeton suivant dans la ligne jusqu’à épuisement des jetons de la ligne. Pour la colorisation, le MPF traite tout le code source comme une séquence de lignes. Par conséquent, le scanneur doit être en mesure de faire face à la source en ligne. En outre, toute ligne peut être transmise au scanneur à tout moment, et la seule garantie est que le moteur d’analyse reçoit la variable d’État à partir de la ligne avant la ligne à analyser.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe est également utilisée pour identifier les déclencheurs de jeton. Ces déclencheurs indiquent au MPF qu’un jeton particulier peut lancer une opération plus complexe, telle que la saisie de mots ou des accolades correspondantes. Étant donné que l’identification de ces déclencheurs doit être rapide et doit se produire à n’importe quel emplacement, le scanneur est mieux adapté à cette tâche.

 Pour plus d’informations, consultez [colorisation de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analyse des fonctionnalités et de la portée
 L’analyse des fonctionnalités et de l’étendue nécessite plus d’efforts que d’identifier simplement les types de jetons rencontrés. L’analyseur doit identifier non seulement le type de jeton, mais également la fonctionnalité pour laquelle le jeton est utilisé. Par exemple, un identificateur est simplement un nom, mais dans votre langage, un identificateur peut être le nom d’une classe, d’un espace de noms, d’une méthode ou d’une variable, selon le contexte. Le type général du jeton peut être un identificateur, mais l’identificateur peut également avoir d’autres significations, en fonction de ce qu’il est et de l’emplacement où il est défini. Cette identification oblige l’analyseur à avoir des connaissances plus étendues sur la langue en cours d’analyse. C’est là qu' <xref:Microsoft.VisualStudio.Package.AuthoringSink> intervient la classe. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe collecte des informations sur les identificateurs, les méthodes, les paires de langages correspondantes (telles que les accolades et les parenthèses) et les triplets de langue (comme les paires de langage, sauf qu’il existe trois parties, par exemple « » et « » `foreach()` `{` `}` ). En outre, vous pouvez substituer la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe pour prendre en charge l’identification du code, qui est utilisé lors de la validation précoce des points d’arrêt afin que le débogueur n’ait pas besoin d’être chargé, et la fenêtre de débogage **automatique** , qui affiche automatiquement les variables et les paramètres locaux lorsqu’un programme est en cours de débogage, et exige que l’analyseur identifie les variables locales et les paramètres appropriés en plus de ceux que le débogueur présente.

 L' <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est passé à l’analyseur dans le cadre de l' <xref:Microsoft.VisualStudio.Package.ParseRequest> objet, et un nouvel <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est créé chaque fois qu’un nouvel <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est créé. En outre, la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode doit retourner un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet, qui est utilisé pour gérer différentes opérations IntelliSense. L' <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet gère une liste pour les déclarations et une liste pour les méthodes, chacune d’elles étant remplie, en fonction de la raison de l’analyse. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe doit être implémentée.

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
