---
title: Legacy Language Service Parser and Scanner (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707312"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanneur et analyseur du service de langage hérité
Le parseur est le cœur du service linguistique. Les cours de langue du Cadre de paquets gérés (MPF) exigent qu’un analyseur de langue sélectionne les informations sur le code affiché. Un analyseur sépare le texte en jetons lexical et identifie ensuite ces jetons par type et fonctionnalité.

## <a name="discussion"></a>Discussions
 Ce qui suit est une méthode de C.

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
|namespace, classe, public, vide, int|mot clé|
|=|operator|
|{ } ( ) ;|delimiter|
|MyNamespace, MyClass, MyFunction, arg1, var1|identificateur|
|MyNamespace (en)|espace de noms|
|MyClass|class|
|MyFunction|method|
|arg1|paramètre|
|var1|variable locale|

 Le rôle du parseur est d’identifier les jetons. Certains jetons peuvent avoir plus d’un type. Une fois que le analyseur a identifié les jetons, le service linguistique peut utiliser les informations pour fournir des fonctionnalités utiles, telles que la mise en évidence de la syntaxe, l’appariement des accolades et les opérations IntelliSense.

## <a name="types-of-parsers"></a>Types de Parsers
 Un analyseur de service linguistique n’est pas le même qu’un analyseur utilisé dans le cadre d’un compilateur. Cependant, ce genre d’analyse doit utiliser à la fois un scanner et un analyseur, de la même manière qu’un analyseur de compilateur.

- Un scanner est utilisé pour identifier les types de jetons. Ces informations sont utilisées pour mettre en surbrillance la syntaxe et identifier rapidement les types de jetons qui peuvent déclencher d'autres opérations, par exemple des accolades correspondantes. Ce scanner est représenté <xref:Microsoft.VisualStudio.Package.IScanner> par l’interface.

- Un analyseur est utilisé pour décrire les fonctions et la portée des jetons. Ces informations sont utilisées dans les opérations d’IntelliSense pour identifier les éléments de langage, tels que les méthodes, les variables, les paramètres et les déclarations, et pour fournir des listes de membres et de signatures de méthodes en fonction du contexte. Ce analyseur est également utilisé pour localiser les paires d’éléments de langage correspondants, telles que les accolades et les parenthèses. Ce analyseur est accessible <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> par la <xref:Microsoft.VisualStudio.Package.LanguageService> méthode de la classe.

  La façon dont vous implémentez un scanner et un analyseur pour votre service linguistique est à vous. Plusieurs ressources sont disponibles qui décrivent comment les analyseurs fonctionnent et comment écrire votre propre analyseur. En outre, plusieurs produits gratuits et commerciaux sont disponibles qui aident à créer un analyseur.

### <a name="the-parsesource-parser"></a>Le ParseSource Parser
 Contrairement à un analyseur qui est utilisé dans le cadre d’un compilateur (où les jetons sont convertis en une certaine forme de code exécutable), un analyseur de service linguistique peut être appelé pour de nombreuses raisons différentes et dans de nombreux contextes différents. La façon dont vous <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> implémentez cette approche dans la méthode de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe est à vous. Il est important de garder <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> à l’esprit que la méthode pourrait être appelée sur un fil de fond.

> [!CAUTION]
> La <xref:Microsoft.VisualStudio.Package.ParseRequest> structure contient une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> référence à l’objet. Cet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet ne peut pas être utilisé dans le thread de fond. En fait, bon nombre des classes MPF de base ne peuvent pas être utilisées dans le fil d’arrière-plan. Il s’agit notamment de la <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> les classes, et toute autre classe qui communique directement ou indirectement avec la vue.

 Cet analyseur analyse généralement le fichier source entière la première fois qu’il <xref:Microsoft.VisualStudio.Package.ParseReason> est appelé ou lorsque la valeur de raison d’analyse de est donnée. Les appels <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ultérieurs à la méthode gèrent une petite partie du code analysé et peuvent être exécutés beaucoup plus rapidement en utilisant les résultats de l’opération d’analyse complète précédente. La <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode communique les résultats de l’opération <xref:Microsoft.VisualStudio.Package.AuthoringScope> d’analyse à travers le et les <xref:Microsoft.VisualStudio.Package.AuthoringSink> objets. L’objet <xref:Microsoft.VisualStudio.Package.AuthoringSink> est utilisé pour recueillir des informations pour une raison d’analyse spécifique, par exemple, des informations sur les travées des accolades correspondantes ou des signatures de méthode qui ont des listes de paramètres. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> fournit des collections de déclarations et de signatures de méthode et également prendre en charge l’option Go To advanced edit (**Go to Definition**, Go to **Declaration**, Go **to Reference**).

### <a name="the-iscanner-scanner"></a>Le scanner IScanner
 Vous devez également implémenter un scanner qui implémente <xref:Microsoft.VisualStudio.Package.IScanner>. Cependant, parce que ce scanner fonctionne sur une <xref:Microsoft.VisualStudio.Package.Colorizer> base ligne par ligne à travers la classe, il est généralement plus facile à mettre en œuvre. Au début de chaque ligne, le <xref:Microsoft.VisualStudio.Package.Colorizer> MPF donne à la classe une valeur à utiliser comme variable d’état qui est transmise au scanner. À la fin de chaque ligne, le scanner retourne la variable d’état mise à jour. Le MPF cache ces informations d’état pour chaque ligne afin que le scanner puisse commencer à analyser à partir de n’importe quelle ligne sans avoir à commencer au début du fichier source. Cette numérisation rapide d’une seule ligne permet à l’éditeur de fournir une rétroaction rapide à l’utilisateur.

## <a name="parsing-for-matching-braces"></a>Parsing pour les accolades assorties
 Cet exemple montre le flux de contrôle pour faire correspondre une attelle de fermeture que l’utilisateur a tapé. Dans ce processus, le scanner qui est utilisé pour la colorisation est également utilisé pour déterminer le type de jeton et si le jeton peut déclencher une opération match-brace. Si le déclencheur est <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> trouvé, la méthode est appelée pour trouver l’attelle assortie. Enfin, les deux accolades sont mises en surbrillance.

 Même si les accolades sont utilisées dans les noms des déclencheurs et des raisons d’analyse, ce processus ne se limite pas aux accolades réelles. Toute paire de caractères spécifiés comme une paire correspondante est prise en charge. Les exemples \< incluent ( et ), et >, et [ et ].

 Supposons que le service linguistique prend en charge les accolades assorties.

1. L’utilisateur tape une accolade bouclée de fermeture ().

2. L’accolade bouclée est insérée au curseur dans le fichier source et le curseur est avancé par un.

3. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode <xref:Microsoft.VisualStudio.Package.Source> dans la classe est appelée avec l’accolade de fermeture dactylographie.

4. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> appelle la <xref:Microsoft.VisualStudio.Package.Source> méthode dans la classe pour obtenir le jeton à la position juste avant la position de curseur actuel. Ce jeton correspond à l’attelle de fermeture dactylographie).

    1. La <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> appelle la <xref:Microsoft.VisualStudio.Package.Colorizer> méthode sur l’objet pour obtenir tous les jetons sur la ligne actuelle.

    2. La <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> appelle la <xref:Microsoft.VisualStudio.Package.IScanner> méthode sur l’objet avec le texte de la ligne actuelle.

    3. La <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode appelle <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> à <xref:Microsoft.VisualStudio.Package.IScanner> plusieurs reprises la méthode sur l’objet pour rassembler tous les jetons de la ligne actuelle.

    4. La <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode appelle une <xref:Microsoft.VisualStudio.Package.Source> méthode privée dans la classe pour obtenir le jeton qui contient la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> position souhaitée, et passe dans la liste des jetons obtenus à partir de la méthode.

5. La <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode recherche un drapeau <xref:Microsoft.VisualStudio.Package.TokenTriggers> de déclenchement symbolique de sur <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> le jeton qui est retourné de la méthode; c’est-à-dire le jeton qui représente l’attelle de clôture).

6. Si le drapeau <xref:Microsoft.VisualStudio.Package.TokenTriggers> de déclenchement <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> de <xref:Microsoft.VisualStudio.Package.Source> est trouvé, la méthode dans la classe est appelée.

7. La <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode commence une opération d’analyse avec <xref:Microsoft.VisualStudio.Package.ParseReason>la valeur de raison d’analyse de . Cette opération appelle <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> finalement <xref:Microsoft.VisualStudio.Package.LanguageService> la méthode sur la classe. Si l’analyse asynchrone est activée, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> cet appel à la méthode se produit sur un fil de fond.

8. Lorsque l’opération d’analyse est terminée, un gestionnaire d’achèvement `HandleMatchBracesResponse` interne (également <xref:Microsoft.VisualStudio.Package.Source> connu sous le nom de méthode de rappel) nommé est appelé dans la classe. Cet appel est effectué <xref:Microsoft.VisualStudio.Package.LanguageService> automatiquement par la classe de base, et non par le parseur.

9. La `HandleMatchBracesResponse` méthode obtient une liste de <xref:Microsoft.VisualStudio.Package.AuthoringSink> travées de <xref:Microsoft.VisualStudio.Package.ParseRequest> l’objet qui est stocké dans l’objet. (Une portée <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> est une structure qui spécifie une gamme de lignes et de caractères dans le fichier source.) Cette liste de travées contient généralement deux travées, une chacune pour les accolades d’ouverture et de fermeture.

10. La `HandleBracesResponse` méthode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> appelle la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> méthode sur l’objet qui est stocké dans l’objet. <xref:Microsoft.VisualStudio.Package.ParseRequest> Cela met en évidence les travées données.

11. Si <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> propriété est `HandleBracesResponse` activée, la méthode obtient le texte qui est englobé par la travée correspondante et affiche les 80 premiers caractères de cette envergure dans la barre d’état. Cela fonctionne mieux <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> si la méthode comprend l’élément de langue qui accompagne la paire correspondante. Pour plus d'informations, consultez la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Opération terminée.

### <a name="summary"></a>Résumé
 L’opération d’accolades assortie est généralement limitée à de simples paires d’éléments de langage. Des éléments plus complexes, tels`if(...)`que`{`des`}`triples`else`assortis`{`("`}`", " et " " " ou " ", " et " " "), peuvent être mis en évidence dans le cadre d’une opération d’achèvement des mots. Par exemple, lorsque le mot « autre`if`» est terminé, la déclaration correspondante « » peut être mise en évidence. S’il y `if` / `else if` avait une série d’énoncés, tous pourraient être mis en évidence en utilisant le même mécanisme que les accolades assorties. La <xref:Microsoft.VisualStudio.Package.Source> classe de base prend déjà en charge cela, <xref:Microsoft.VisualStudio.Package.TokenTriggers> comme suit: <xref:Microsoft.VisualStudio.Package.TokenTriggers> Le scanner doit retourner la valeur de déclenchement symbolique combiné avec la valeur de déclenchement pour le jeton qui est avant la position du curseur.

 Pour plus d’informations, voir [Brace Matching in a Legacy Language Service](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Parsing pour colorisation
 Colorizing code source est simple, il suffit d’identifier le type de jeton et retourner des informations de couleur sur ce type. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe agit comme l’intermédiaire entre l’éditeur et le scanner pour fournir des informations de couleur sur chaque jeton. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe <xref:Microsoft.VisualStudio.Package.IScanner> utilise l’objet pour aider à coloriser une ligne et aussi pour recueillir des informations d’état pour toutes les lignes dans le fichier source. Dans les cours de service <xref:Microsoft.VisualStudio.Package.Colorizer> linguistique MPF, la classe n’a pas à <xref:Microsoft.VisualStudio.Package.IScanner> être remplacée parce qu’elle communique avec le scanner uniquement par l’interface. Vous fournissez l’objet <xref:Microsoft.VisualStudio.Package.IScanner> qui implémente l’interface en l’emporteant sur la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.

 Le <xref:Microsoft.VisualStudio.Package.IScanner> scanner reçoit une ligne de <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> code source par la méthode. Les appels <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> à la méthode sont répétés pour obtenir le jeton suivant dans la ligne jusqu’à ce que la ligne soit épuisée des jetons. Pour la colorisation, le MPF traite tout le code source comme une séquence de lignes. Par conséquent, le scanner doit être en mesure de faire face à la source venant à elle comme des lignes. En outre, n’importe quelle ligne peut être passée au scanner à tout moment, et la seule garantie est que le scanner reçoit la variable d’état de la ligne avant que la ligne sur le point d’être numérisée.

 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe est également utilisée pour identifier les déclencheurs symboliques. Ces déclencheurs indiquent au MPF qu’un jeton particulier peut initier une opération plus complexe, comme l’achèvement des mots ou des accolades assorties. Parce que l’identification de tels déclencheurs doit être rapide et doit se produire à n’importe quel endroit, le scanner est le mieux adapté à cette tâche.

 Pour plus d’informations, voir [Syntax Colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Parsing pour la fonctionnalité et la portée
 Le parsage pour la fonctionnalité et la portée exige plus d’effort que simplement identifier les types de jetons qui sont rencontrés. Le analyseur doit identifier non seulement le type de jeton, mais aussi la fonctionnalité pour laquelle le jeton est utilisé. Par exemple, un identifiant n’est qu’un nom, mais dans votre langue, un identifiant peut être le nom d’une classe, d’un espace de nom, d’une méthode ou d’une variable, selon le contexte. Le type général du jeton peut être un identifiant, mais l’identifiant peut également avoir d’autres significations, selon ce qu’il est et où il est défini. Cette identification exige que l’analyseur ait des connaissances plus approfondies sur la langue qui est analysée. C’est <xref:Microsoft.VisualStudio.Package.AuthoringSink> là que la classe entre en vigueur. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe recueille des informations sur les identificateurs, les méthodes, les paires de langage assorties (comme les accolades`foreach()`et`{`les parenthèses), et les triples linguistiques (semblables aux paires de langues, sauf qu’il y a trois parties, par exemple, « « » et «`}`» En outre, vous pouvez <xref:Microsoft.VisualStudio.Package.AuthoringSink> remplacer la classe pour prendre en charge l’identification du code, qui est utilisé dans la validation précoce des points d’arrêt de sorte que le débbuggeur n’a pas à être chargé, et la fenêtre de débogage **Autos,** qui montre les variables locales et les paramètres automatiquement quand un programme est débugged et exige que le analyseur d’identifier les variables locales appropriées et les paramètres en plus de ceux que le débogage présente.

 L’objet <xref:Microsoft.VisualStudio.Package.AuthoringSink> est transmis au parseur dans le cadre de l’objet, <xref:Microsoft.VisualStudio.Package.ParseRequest> et un nouvel <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est créé chaque fois qu’un nouvel <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est créé. En outre, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> la méthode <xref:Microsoft.VisualStudio.Package.AuthoringScope> doit retourner un objet, qui est utilisé pour gérer diverses opérations IntelliSense. L’objet <xref:Microsoft.VisualStudio.Package.AuthoringScope> maintient une liste de déclarations et une liste pour les méthodes, dont l’un ou l’autre est peuplé, selon la raison de l’analyse. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe doit être mise en œuvre.

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)
- [Couleurs de syntaxe dans un service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
