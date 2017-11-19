---
title: "Analyseur de Service de langage hérité et Analyseur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30453237dcd95607a4f3524f115d16bc1cf4859a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analyseur et l’Analyseur de Service de langage hérité
L’analyseur est au cœur du service de langage. Les classes de langage Managed Package Framework (MPF) requièrent un analyseur de langage pour sélectionner plus d’informations sur le code qui est affiché. Un analyseur sépare le texte en jetons lexicaux et identifie ces jetons par type et de fonctionnalités.  
  
## <a name="discussion"></a>Discussion  
 Voici une méthode c#.  
  
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
  
 Dans cet exemple, les jetons sont les mots et les signes de ponctuation. Les types de jetons sont les suivantes.  
  
|Nom du jeton|Type de jeton|  
|----------------|----------------|  
|espace de noms, void publique, classe, int|keyword|  
|=|opérateur|  
|{ } ( ) ;|Délimiteur|  
|MyNamespace, MyClass, MyFunction, arg1, var1|'identificateur'|  
|MyNamespace|namespace|  
|MyClass|class|  
|MyFunction|méthode|  
|arg1|paramètre|  
|var1|variable locale|  
  
 Le rôle de l’analyseur est d’identifier les jetons. Certains jetons peuvent avoir plusieurs types. Une fois que l’analyseur a identifié les jetons, le service de langage peut utiliser les informations pour fournir des fonctionnalités utiles, telles que la mise en surbrillance de syntaxe, la correspondance des accolades et les opérations d’IntelliSense.  
  
## <a name="types-of-parsers"></a>Types d’analyseurs  
 Un analyseur de service de langage n’est pas identique à un analyseur utilisé dans le cadre d’un compilateur. Toutefois, ce type d’analyseur doit utiliser un analyseur et un analyseur, de la même façon en tant qu’un analyseur du compilateur.  
  
-   Un analyseur est utilisé pour identifier les types de jetons. Ces informations sont utilisées pour mettre en surbrillance de la syntaxe et identifier rapidement les types de jetons qui peuvent déclencher d’autres opérations, par exemple, la correspondance des accolades. Cet analyseur est représenté par la <xref:Microsoft.VisualStudio.Package.IScanner> interface.  
  
-   Un analyseur est utilisé pour décrire les fonctions et l’étendue des jetons. Ces informations sont utilisées dans les opérations d’IntelliSense pour identifier les éléments de langage, telles que les méthodes, les variables, les paramètres et les déclarations et pour fournir des listes de membres et les signatures de méthode selon le contexte. Cet analyseur est également utilisé pour localiser des paires d’éléments de langage correspondant, tels que des accolades et des parenthèses. Cet analyseur est accessible via la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Comment implémenter un moteur d’analyse et de l’analyseur pour votre service de langage il vous revient. Plusieurs ressources sont disponibles qui décrivent le fonctionnement des analyseurs et comment écrire votre propre analyseur. En outre, plusieurs produits commerciales et libres sont disponibles qui vous aidera à créer un analyseur.  
  
### <a name="the-parsesource-parser"></a>L’analyseur ParseSource  
 Contrairement à un analyseur qui est utilisé en tant que partie d’un compilateur (où les jetons sont converties en une forme de code exécutable), un analyseur de service de langage peut être appelé pour de nombreuses raisons et dans de nombreux contextes différents. Comment vous implémentez cette approche dans les <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe vous revient. Il est important de garder à l’esprit que le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode peut être appelée sur un thread d’arrière-plan.  
  
> [!CAUTION]
>  Le <xref:Microsoft.VisualStudio.Package.ParseRequest> structure contient une référence à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet. Cela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet ne peut pas être utilisé dans le thread d’arrière-plan. En fait, de nombreuses classes MPF base ne peut pas être utilisés dans le thread d’arrière-plan. Celles-ci incluent la <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classes et toute autre classe directement ou indirectement communique avec la vue.  
  
 Cet analyseur analyse généralement l’heure de fichier la première source complète, elle est appelée ou lorsque l’analyse de la raison valeur de <xref:Microsoft.VisualStudio.Package.ParseReason> est donnée. Les appels suivants à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode gérer une petite partie du code analysé et peuvent être exécutées plus rapidement en utilisant les résultats de l’opération d’analyse complète précédente. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode communique les résultats de l’opération d’analyse via le <xref:Microsoft.VisualStudio.Package.AuthoringSink> et <xref:Microsoft.VisualStudio.Package.AuthoringScope> objets. Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est utilisé pour collecter des informations pour une raison donnée d’analyse, par exemple, les informations sur les étendues des accolades ou des signatures de méthode qui ont des listes de paramètres. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> fournit des collections de déclarations ainsi que les signatures de méthode et prise en charge pour aller à avancée modifier l’option (**atteindre la définition**, **atteindre la déclaration**, **atteindre Référence**).  
  
### <a name="the-iscanner-scanner"></a>L’analyseur IScanner  
 Vous devez également implémenter un analyseur qui implémente <xref:Microsoft.VisualStudio.Package.IScanner>. Toutefois, étant donné que cet analyseur opère une ligne par ligne via la <xref:Microsoft.VisualStudio.Package.Colorizer> (classe), il est généralement plus facile à implémenter. Au début de chaque ligne, MPF donne le <xref:Microsoft.VisualStudio.Package.Colorizer> une valeur à utiliser comme une variable d’état qui est transmise à l’Analyseur de la classe. À la fin de chaque ligne, l’analyseur renvoie la variable d’état de mise à jour. MPF met en cache ces informations d’état pour chaque ligne afin que le moteur d’analyse puisse commencer l’analyse à partir de n’importe quelle ligne sans avoir à commencer au début du fichier source. Cette analyse rapide d’une ligne unique permet à l’éditeur fournir des commentaires rapides à l’utilisateur.  
  
## <a name="parsing-for-matching-braces"></a>L’analyse pour la correspondance des accolades  
 Cet exemple montre le flux de contrôle pour la correspondance d’accolade fermante tapé par l’utilisateur. Dans ce processus, le moteur d’analyse qui est utilisé pour la colorisation est également utilisé pour déterminer le type de jeton et indique si le jeton peut déclencher une opération accolade de correspondance. Si le déclencheur est trouvé, le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est appelée pour rechercher l’accolade correspondante. Enfin, les deux accolades sont mises en surbrillance.  
  
 Bien que les accolades sont utilisés dans les noms de déclencheurs et analyser les raisons, ce processus n’est pas limité à des accolades réels. N’importe quelle paire de caractères qui est spécifiée pour être mise en correspondance une paire est pris en charge. Exemples (et), \< et >, et [et].  
  
 Supposons que le service de langage prend en charge les accolades correspondantes.  
  
1.  L’utilisateur tape une accolade fermante (}).  
  
2.  L’accolade est insérée au niveau du curseur dans le fichier source et le curseur s’avance d’une unité.  
  
3.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée avec l’accolade fermante typé.  
  
4.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton à la position juste avant la position actuelle du curseur. Ce jeton correspond à l’accolade fermante typé).  
  
    1.  Le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Colorizer> pour obtenir tous les jetons de la ligne actuelle.  
  
    2.  Le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.IScanner> objet avec le texte de la ligne actuelle.  
  
    3.  Le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode appelle à plusieurs reprises la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.IScanner> objet pour collecter tous les jetons à partir de la ligne actuelle.  
  
    4.  Le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> appelle une méthode privée le <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton qui contient la position voulue et passe dans la liste des jetons obtenu à partir de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> (méthode).  
  
5.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode recherche un indicateur de déclencheur d’émission de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton qui est retourné à partir de la <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> (méthode), autrement dit, le jeton qui représente l’accolade fermante).  
  
6.  Si le déclencheur indicateur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> est trouvée, le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée.  
  
7.  Le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode démarre une opération d’analyse avec la valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Cette opération appelle finalement la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Si l’analyse d’asynchrone est activé, cet appel à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode se produit sur un thread d’arrière-plan.  
  
8.  Lorsque l’opération d’analyse est terminée, un gestionnaire d’achèvement interne (également appelé une méthode de rappel) nommé `HandleMatchBracesResponse` est appelée dans la <xref:Microsoft.VisualStudio.Package.Source> classe. Cet appel est effectué automatiquement par le <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base, pas par l’analyseur.  
  
9. Le `HandleMatchBracesResponse` méthode pour obtenir une liste d’étendues à partir de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet qui est stocké dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. (Une étendue est un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> structure qui spécifie une plage de lignes et de caractères dans le fichier source.) Cette liste d’étendues contient généralement deux étendues, une pour les accolades ouvrantes et fermantes.  
  
10. Le `HandleBracesResponse` les appels de méthode le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet qui est stocké dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. Cela met en évidence les étendues donnés.  
  
11. Si le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> est activé, le `HandleBracesResponse` méthode obtient le texte qui est englobé par l’étendue correspondante et affiche les 80 premiers caractères de cette étendue dans la barre d’état. Cela fonctionne mieux si les <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode inclut l’élément de langage qui accompagne le couple. Pour plus d'informations, consultez la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Opération effectuée.  
  
### <a name="summary"></a>Résumé  
 L’opération d’accolades correspondante est généralement limitée à des paires simples des éléments de langage. D’éléments plus complexes, telles que la mise en correspondance triplets («`if(...)`«, »`{`« et »`}`», ou «`else`«, »`{`« et »`}`»), peut être mis en surbrillance dans le cadre d’une opération de saisie semi-automatique par word. Par exemple, lorsque le mot « else » est terminé, la mise en correspondance «`if`» instruction peut être mise en surbrillance. S’il existait une série de `if` / `else if` instructions, tous les peuvent être mis en surbrillance à l’aide du même mécanisme de correspondance des accolades. Le <xref:Microsoft.VisualStudio.Package.Source> classe de base prend déjà en charge, comme suit : l’analyseur doit retourner la valeur de jeton déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinée avec la valeur de déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour le jeton qui est antérieure à la position du curseur.  
  
 Pour plus d’informations, consultez [accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>L’analyse de colorisation  
 Colorisation de code source est simple, seulement identifier le type d’informations de couleur de jeton et de retour sur ce type. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe agit comme intermédiaire entre l’éditeur et le moteur d’analyse pour fournir des informations de couleur sur chaque jeton. Le <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilise le <xref:Microsoft.VisualStudio.Package.IScanner> objet pour faciliter la colorisation une ligne et également pour recueillir des informations d’état pour toutes les lignes dans le fichier source. Dans les classes de service de langage MPF, le <xref:Microsoft.VisualStudio.Package.Colorizer> classe n’a pas à être remplacé, car il communique avec le moteur d’analyse uniquement via la <xref:Microsoft.VisualStudio.Package.IScanner> interface. Vous fournissez l’objet qui implémente le <xref:Microsoft.VisualStudio.Package.IScanner> interface en substituant le <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Le <xref:Microsoft.VisualStudio.Package.IScanner> analyseur reçoit une ligne de code source via le <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> (méthode). Les appels à la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sont répétées pour obtenir le jeton suivant dans la ligne jusqu'à épuisée de la ligne de jetons. Pour la colorisation, MPF traite tout le code source comme une séquence de lignes. Par conséquent, le moteur d’analyse doit être en mesure de faire face à la source à venir lui sous forme de lignes. En outre, n’importe quelle ligne peut être transmis à l’analyseur à tout moment, et la seule garantie est que l’analyseur reçoit la variable d’état à partir de la ligne avant la ligne sur le point d’être analysés.  
  
 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe est également utilisée pour identifier les déclencheurs de jeton. Ces déclencheurs indiquent MPF qu’un jeton donné peut initier une opération plus complexe, par exemple mot, compléter ou la correspondance des accolades. Identification de ces déclencheurs doit être rapide et doit se produire à n’importe quel emplacement, l’analyseur est parfaitement adapté pour cette tâche.  
  
 Pour plus d’informations, consultez [coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>L’analyse de fonctionnalité et de portée  
 L’analyse de fonctionnalité et de portée nécessite plus d’efforts que qui identifie les types de jetons sont rencontrées. L’analyseur a identifier le type de jeton, mais également les fonctionnalités pour lequel le jeton est utilisé. Par exemple, un identificateur est simplement un nom, mais dans votre langue, un identificateur peut être le nom d’une classe, un espace de noms, une méthode ou une variable, en fonction du contexte. Le type général du jeton peut être un identificateur, mais l’identificateur peut avoir également d’autres significations, selon qu’il est, et dans laquelle il est défini. Cette identification nécessite l’analyseur d’avoir des connaissances plus étendues sur le langage qui est en cours d’analyse. C’est là la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe est fournie. Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe recueille des informations sur les identificateurs, les méthodes, les paires correspondantes de langage (tels que les accolades et des parenthèses) et langage triplets (similaires à des paires de langue, sauf qu’il existe trois parties, par exemple, «`foreach()`» «`{`« et »`}`»). En outre, vous pouvez remplacer le <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe prenne en charge l’identification de code, qui est utilisée pour la validation de liaison anticipée des points d’arrêt afin que le débogueur n’ait pas à charger, et le **automatique** fenêtre de débogage, qui affiche local variables et paramètres automatiquement lorsqu’un programme est en cours de débogage et nécessite l’analyseur pour identifier des variables locales appropriées et les paramètres en plus de ceux que le débogueur présente.  
  
 Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est passé à l’analyseur dans le cadre de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objet, ainsi qu’un nouveau <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est créée chaque fois qu’un nouveau <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est créé. En outre, le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode doit retourner un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet, qui est utilisé pour gérer diverses opérations IntelliSense. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet gère une liste de déclarations et une liste de méthodes, soit qui est rempli, selon la raison de l’analyse. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe doit être implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Vue d’ensemble du Service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)   
 [Coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)