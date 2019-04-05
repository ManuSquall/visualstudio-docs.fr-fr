---
title: Analyseur de Service de langage hérité et le moteur d’analyse | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5110c0289a630640fdb2c2383234173d931c72
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950254"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanneur et analyseur du service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’analyseur est le cœur du service de langage. Les classes de langage de Managed Package Framework (MPF) nécessitent un analyseur de langage pour sélectionner des informations sur le code affiché. Un analyseur sépare le texte en jetons lexicaux et identifie ces jetons par type et de fonctionnalités.  
  
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
  
 Dans cet exemple, les jetons sont les mots et les signes de ponctuation. Les types de jetons sont comme suit.  
  
|Nom du jeton|Type de jeton|  
|----------------|----------------|  
|namespace, class, public, void, int|keyword|  
|=|operator|  
|{ } ( ) ;|délimiteur|  
|MyNamespace, MyClass, MyFunction, arg1, var1|'identificateur'|  
|MyNamespace|namespace|  
|MyClass|class|  
|MyFunction|méthode|  
|arg1|paramètre|  
|var1|variable locale|  
  
 Le rôle de l’analyseur consiste à identifier les jetons. Bien que certains jetons peuvent avoir plusieurs types. Une fois que l’analyseur a identifié les jetons, le service de langage peut utiliser les informations pour fournir des fonctionnalités utiles, telles que la coloration syntaxique, correspondance des accolades et les opérations IntelliSense.  
  
## <a name="types-of-parsers"></a>Types d’analyseurs  
 Un analyseur de service de langage n’est pas identique à un analyseur utilisé dans le cadre d’un compilateur. Toutefois, ce type d’analyseur doit utiliser un analyseur et un analyseur, dans la même façon que d’un analyseur du compilateur.  
  
- Un scanneur est utilisé pour identifier les types de jetons. Ces informations sont utilisées pour mettre en surbrillance la syntaxe et identifier rapidement les types de jetons qui peuvent déclencher d'autres opérations, par exemple des accolades correspondantes. Ce scanneur est représenté par le <xref:Microsoft.VisualStudio.Package.IScanner> interface.  
  
- Un analyseur est utilisé pour décrire les fonctions et l’étendue des jetons. Ces informations sont utilisées dans les opérations IntelliSense pour identifier les éléments de langage, tels que les méthodes, les variables, les paramètres et les déclarations et pour fournir des listes de membres et les signatures de méthode en fonction du contexte. Cet analyseur est également utilisé pour localiser des paires d’éléments de langage correspondant, tels que des accolades et des parenthèses. Cet analyseur est accessible via la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
  Comment implémenter un scanneur et l’analyseur pour votre service de langage vous revient. Plusieurs ressources sont disponibles qui décrivent le fonctionnement des analyseurs et comment écrire votre propre analyseur. En outre, plusieurs produits gratuits et commerciaux sont disponibles qui facilite la création d’un analyseur.  
  
### <a name="the-parsesource-parser"></a>L’analyseur ParseSource  
 Contrairement à un analyseur qui est utilisé dans le cadre d’un compilateur (où les jetons sont converties en une forme de code exécutable), un analyseur de service de langage peut être appelé pour de nombreuses raisons et dans de nombreux contextes différents. Comment implémenter cette approche dans les <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe vous revient. Il est important de garder à l’esprit que le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode peut être appelée sur un thread d’arrière-plan.  
  
> [!CAUTION]
>  Le <xref:Microsoft.VisualStudio.Package.ParseRequest> structure contient une référence à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet. Cela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet ne peut pas être utilisé dans le thread d’arrière-plan. En fait, de nombreuses classes MPF base ne peut pas être utilisés dans le thread d’arrière-plan. Ceux-ci incluent le <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classes et toute autre classe directement ou indirectement communique avec la vue.  
  
 Cet analyseur analyse généralement l’heure de fichier la première source complète, elle est appelée ou lorsque l’analyse de la raison valeur de <xref:Microsoft.VisualStudio.Package.ParseReason> est donné. Les appels suivants à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode gérer une petite partie du code analysé et peuvent être exécutées beaucoup plus rapidement en utilisant les résultats de l’opération d’analyse complète précédente. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode communique les résultats de l’opération d’analyse via le <xref:Microsoft.VisualStudio.Package.AuthoringSink> et <xref:Microsoft.VisualStudio.Package.AuthoringScope> objets. Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est utilisé pour collecter des informations pour une raison donnée d’analyse, par exemple, les informations sur les étendues de mise en correspondance d’accolades ou de signatures de méthode qui ont des listes de paramètres. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> fournit des collections de déclarations et les signatures de méthode et également prise en charge pour aller à avancé modifier l’option (**atteindre la définition**, **atteindre la déclaration**, **atteindre Référence**).  
  
### <a name="the-iscanner-scanner"></a>Le scanneur IScanner  
 Vous devez également implémenter un analyseur qui implémente <xref:Microsoft.VisualStudio.Package.IScanner>. Toutefois, étant donné que ce scanneur opère une ligne par ligne via le <xref:Microsoft.VisualStudio.Package.Colorizer> (classe), il est généralement plus facile à implémenter. Au début de chaque ligne, le MPF donne le <xref:Microsoft.VisualStudio.Package.Colorizer> une valeur à utiliser comme une variable d’état qui est transmise à l’Analyseur de classe. À la fin de chaque ligne, le scanneur retourne la variable d’état de mise à jour. MPF met en cache ces informations d’état pour chaque ligne afin que le scanneur puisse commencer l’analyse à partir de n’importe quelle ligne sans avoir à commencer au début du fichier source. Cette analyse rapide d’une seule ligne permet à l’éditeur pour fournir des commentaires rapides à l’utilisateur.  
  
## <a name="parsing-for-matching-braces"></a>L’analyse pour les accolades correspondantes  
 Cet exemple montre le flux de contrôle pour la mise en correspondance une accolade fermante saisi par l’utilisateur a. Dans ce processus, le moteur d’analyse qui est utilisé pour la colorisation est également utilisé pour déterminer le type de jeton et indique si le jeton peut déclencher une opération d’accolade de correspondance. Si le déclencheur est trouvé, le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est appelée pour rechercher l’accolade correspondante. Enfin, les deux accolades sont mises en surbrillance.  
  
 Même si les accolades sont utilisés dans les noms de déclencheurs et d’analyser les raisons, ce processus n’est pas limité aux accolades réelles. Toute paire de caractères qui est spécifiée comme étant une paire correspondante est pris en charge. Exemples (et), \< et >, et [et].  
  
 Partons du principe que le service de langage prend en charge les accolades correspondantes.  
  
1.  L’utilisateur tape une accolade fermante (}).  
  
2.  L’accolade est insérée au niveau du curseur dans le fichier source et le curseur est avancé d’une unité.  
  
3.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée avec l’accolade fermante typé.  
  
4.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton à la position juste avant la position actuelle du curseur. Ce jeton correspond à l’accolade fermante typé).  
  
    1.  Le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Colorizer> objet pour obtenir tous les jetons de la ligne actuelle.  
  
    2.  Le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> les appels de méthode le <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.IScanner> objet avec le texte de la ligne active.  
  
    3.  Le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode appelle à plusieurs reprises la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.IScanner> objet à rassembler tous les jetons à partir de la ligne actuelle.  
  
    4.  Le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode appelle une méthode privée le <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton qui contient la position voulue et passe dans la liste des jetons obtenus à partir de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> (méthode).  
  
5.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode recherche un indicateur de jetons de déclencheur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton qui est retourné à partir de la <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode ; autrement dit, le jeton qui représente l’accolade fermante).  
  
6.  Si le déclencheur indicateur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> est trouvée, le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée.  
  
7.  Le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode démarre une opération d’analyse avec la valeur de motif de l’analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Cette opération appelle finalement la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Si l’analyse asynchrone est activé, cet appel à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode se produit sur un thread d’arrière-plan.  
  
8.  Lorsque l’opération d’analyse est terminée, un gestionnaire d’achèvement interne (également appelé une méthode de rappel) nommé `HandleMatchBracesResponse` est appelée le <xref:Microsoft.VisualStudio.Package.Source> classe. Cet appel est effectué automatiquement par le <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base, pas par l’analyseur.  
  
9. Le `HandleMatchBracesResponse` méthode obtient une liste d’étendues à partir de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet qui est stocké dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. (Une étendue est un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> structure qui spécifie une plage de lignes et de caractères dans le fichier source.) Cette liste d’étendues contient généralement deux étendues, une pour les accolades ouvrantes et fermantes.  
  
10. Le `HandleBracesResponse` les appels de méthode le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet qui est stocké dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. Cela met en évidence les étendues donnés.  
  
11. Si le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> est activé, le `HandleBracesResponse` méthode obtient le texte qui est englobé par l’étendue correspondante et affiche des 80 premiers caractères de cette étendue dans la barre d’état. Cela fonctionne mieux si le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode inclut l’élément de langage qui accompagne la paire correspondante. Pour plus d'informations, consultez la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Terminé.  
  
### <a name="summary"></a>Récapitulatif  
 L’opération d’accolades correspondante est généralement limitée à simples paires d’éléments de langage. Des éléments plus complexes, telles que la mise en correspondance triplets («`if(…)`«, »`{`« et »`}`», ou «`else`«, »`{`« et »`}`»), peut être mis en surbrillance dans le cadre d’une opération de saisie semi-automatique par word. Par exemple, lorsque le mot « else » est terminé, la mise en correspondance «`if`» instruction peut être mis en surbrillance. S’il y avait une série de `if` / `else if` instructions, tous les peuvent être mis en surbrillance à l’aide du même mécanisme comme accolades correspondantes. Le <xref:Microsoft.VisualStudio.Package.Source> classe de base prend déjà en charge, comme suit : L’analyseur doit retourner la valeur du jeton de déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinée avec la valeur de déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour le jeton qui se trouve avant la position du curseur.  
  
 Pour plus d’informations, consultez [accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>L’analyse pour la colorisation  
 Colorisation de code source est simple, seulement identifier le type d’informations de couleur de jeton et de retour sur ce type. Le <xref:Microsoft.VisualStudio.Package.Colorizer> classe agit comme intermédiaire entre l’éditeur et le moteur d’analyse pour fournir des informations de couleur sur chaque jeton. Le <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilise le <xref:Microsoft.VisualStudio.Package.IScanner> objet pour vous aider dans la colorisation une ligne et également pour recueillir des informations d’état pour toutes les lignes dans le fichier source. Dans les classes de service de langage MPF, le <xref:Microsoft.VisualStudio.Package.Colorizer> classe ne doit pas être remplacé, car il communique avec le scanner uniquement via le <xref:Microsoft.VisualStudio.Package.IScanner> interface. Vous fournissez l’objet qui implémente le <xref:Microsoft.VisualStudio.Package.IScanner> interface en substituant le <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Le <xref:Microsoft.VisualStudio.Package.IScanner> scanneur est fonction d’une ligne de code source via le <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> (méthode). Les appels à la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sont répétées pour obtenir le jeton suivant dans la ligne jusqu'à épuisée de la ligne de jetons. Pour la colorisation, MPF traite tout le code source comme une séquence de lignes. Par conséquent, le moteur d’analyse doit être en mesure de faire face à la source arrive à elle sous forme de lignes. En outre, n’importe quelle ligne peut être passée au scanneur à tout moment, et la seule garantie est que le scanneur reçoit la variable d’état de la ligne avant la ligne sur le point d’être analysés.  
  
 Le <xref:Microsoft.VisualStudio.Package.Colorizer> classe est également utilisée pour identifier les déclencheurs de jeton. Ces déclencheurs indiquent le MPF qu’un jeton donné peut initier une opération plus complexe, comme la saisie semi-automatique de mot ou d’accolades correspondantes. Étant donné qu’identifier ces déclencheurs doit être rapide et doit se produire à n’importe quel emplacement, le scanneur est idéal pour cette tâche.  
  
 Pour plus d’informations, consultez [couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>L’analyse de fonctionnalité et de portée  
 L’analyse de fonctionnalité et de portée nécessite plus d’efforts qu’identifie les types de jetons qui sont rencontrées. L’analyseur a identifier le type de jeton, mais également la fonctionnalité pour laquelle le jeton est utilisé. Par exemple, un identificateur est simplement un nom, mais dans votre langue, un identificateur peut être le nom d’une classe, un espace de noms, une méthode ou une variable, en fonction du contexte. Le type général du jeton peut être un identificateur, mais l’identificateur peut avoir également d’autres significations, selon qu’il s’agit et où il est défini. Cette identification nécessite l’analyseur pour ont une connaissance approfondie de la langue qui est en cours d’analyse. C’est là le <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe est fournie. Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe recueille des informations sur les identificateurs, les méthodes, les paires correspondantes de langage (tels que des accolades et des parenthèses) et les triples de langage (similaire à des paires de langages, à ceci près qu’il existe trois parties, par exemple, «`foreach()`» «`{`« et »`}`»). En outre, vous pouvez remplacer le <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe pour prendre en charge d’identification du code, qui est utilisée dans les premières validations de points d’arrêt afin que le débogueur ne devra pas être chargé, et le **automatique** fenêtre de débogage, montre local variables et paramètres automatiquement quand un programme est en cours de débogage et nécessite l’analyseur pour identifier des variables locales appropriées et les paramètres en plus de ceux qui présente le débogueur.  
  
 Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est passé à l’analyseur dans le cadre de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objet et un nouveau <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est créée chaque fois qu’un nouveau <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est créé. En outre, le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode doit retourner un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet, qui permet de gérer diverses opérations IntelliSense. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet conserve une liste des déclarations et une liste de méthodes, soit de ce qui est remplie, selon la raison pour l’analyse. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe doit être implémentée.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Vue d’ensemble du Service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)   
 [Couleurs de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Accolades correspondantes dans un service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
