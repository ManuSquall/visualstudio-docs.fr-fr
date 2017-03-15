---
title: "Scanneur et analyseur du Service de langage ancien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyseurs, des services de langage (framework package managé)"
  - "services de langage (framework package managé), les analyseurs"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Scanneur et analyseur du Service de langage ancien
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'analyseur est le cœur du service de langage. Les classes de langage Managed Package Framework \(MPF\) requièrent un analyseur de langage pour sélectionner les informations sur le code affiché. Un analyseur sépare le texte en jetons lexicaux et identifie les jetons par type et de fonctionnalités.  
  
## Discussion  
 Voici une méthode c\#.  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 Dans cet exemple, les jetons sont les mots et les signes de ponctuation. Voici les types de jetons.  
  
|Nom du jeton|Type de jeton|  
|------------------|-------------------|  
|void publique, classe, espace de noms int|keyword|  
|\=|operator|  
|{ } \( \) ;|délimiteur|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|  
|MyNamespace|namespace|  
|MyClass|classe|  
|MyFunction|méthode|  
|arg1|paramètre|  
|var1|variable locale|  
  
 Le rôle de l'analyseur consiste à identifier les jetons. Certains jetons peuvent avoir plusieurs types. Une fois que l'analyseur a identifié les jetons, le service de langage peut utiliser les informations pour fournir des fonctionnalités utiles, telles que la mise en évidence, la correspondance des accolades et les opérations d'IntelliSense.  
  
## Types d'analyseurs  
 Un analyseur de service de langage n'est pas identique à un analyseur utilisé dans le cadre d'un compilateur. Toutefois, ce type d'analyseur doit utiliser un scanner et un analyseur, dans la même façon que l'analyseur du compilateur.  
  
-   Un scanneur est utilisé pour identifier les types de jetons. Ces informations sont utilisées pour mettre en surbrillance de la syntaxe et identifier rapidement les types de jetons qui peuvent déclencher d'autres opérations, par exemple, accolades correspondantes. Cet analyseur est représenté par la <xref:Microsoft.VisualStudio.Package.IScanner> interface.  
  
-   Celui\-ci est utilisé pour décrire les fonctions et l'étendue des jetons. Ces informations sont utilisées dans les opérations d'IntelliSense pour identifier les éléments de langage, telles que les méthodes, les variables, les paramètres et les déclarations et pour fournir des listes de membres et signatures de méthode selon le contexte. Cet analyseur est également utilisé pour localiser des paires d'éléments de langage correspondant, tels que des accolades et des parenthèses. Cet analyseur est accessible via la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Comment implémenter un scanneur et l'analyseur pour votre service de langage vous revient. Plusieurs ressources sont disponibles qui décrivent le fonctionnement des analyseurs et comment écrire votre propre analyseur. En outre, plusieurs produits gratuits et commerciaux sont disponibles qui facilite la création d'un analyseur.  
  
### L'analyseur ParseSource  
 Contrairement à un analyseur qui est utilisé dans le cadre d'un compilateur \(où les jetons sont converties en une forme de code exécutable\), un analyseur de service de langage peut être appelé pour de nombreuses raisons et dans de nombreux contextes différents. Comment implémenter cette approche dans la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe vous revient. Il est important de garder à l'esprit que le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode peut être appelée sur un thread d'arrière\-plan.  
  
> [!CAUTION]
>  Le <xref:Microsoft.VisualStudio.Package.ParseRequest> structure contient une référence à la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet. Cela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet ne peut pas être utilisé dans le thread d'arrière\-plan. En fait, plusieurs classes de base MPF ne peut pas être utilisés dans le thread d'arrière\-plan. Ceux\-ci incluent le <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classes et toute autre classe directement ou indirectement communique avec la vue.  
  
 Cet analyseur analyse généralement l'heure de fichier la première source complète qu'elle est appelée ou lorsque l'analyse de la valeur de la raison <xref:Microsoft.VisualStudio.Package.ParseReason> est donné. Les appels suivants à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode gérer une petite partie de code analysé et peuvent être exécutées plus rapidement en utilisant les résultats de l'opération d'analyse complète précédente. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode communique les résultats de l'opération d'analyse par le biais du <xref:Microsoft.VisualStudio.Package.AuthoringSink> et <xref:Microsoft.VisualStudio.Package.AuthoringScope> objets. Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est utilisé pour collecter des informations pour une raison spécifique d'analyse, par exemple, les informations sur les étendues des accolades ou des signatures de méthode qui ont des listes de paramètres. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> fournit des collections de déclarations et les signatures de méthode et prend en charge pour les atteindre les avancées de modifier l'option \(**Atteindre la définition**, **Atteindre la déclaration**, **Atteindre la référence**\).  
  
### L'analyseur IScanner  
 Vous devez également implémenter un analyseur qui implémente <xref:Microsoft.VisualStudio.Package.IScanner>. Toutefois, étant donné que cette analyse fonctionne sur une base ligne par ligne via la <xref:Microsoft.VisualStudio.Package.Colorizer> classe, il est généralement plus facile à implémenter. Au début de chaque ligne, le MPF donne le <xref:Microsoft.VisualStudio.Package.Colorizer> une valeur à utiliser comme une variable d'état qui est transmise à l'Analyseur de la classe. À la fin de chaque ligne, l'analyseur retourne la variable d'état de mise à jour. Le MPF met en cache ces informations d'état pour chaque ligne afin que l'analyseur puisse commencer l'analyse à partir de n'importe quelle ligne, sans avoir à commencer au début du fichier source. Cette analyse rapide d'une seule ligne permet à l'éditeur fournir des commentaires rapides à l'utilisateur.  
  
## L'analyse pour la correspondance des accolades  
 Cet exemple illustre le flux de contrôle pour la mise en correspondance une accolade fermante tapé par l'utilisateur. Dans ce processus, le moteur d'analyse qui est utilisé pour la colorisation est également utilisé pour déterminer le type de jeton et indique si le jeton peut déclencher une opération d'accolade de correspondance. Si le déclencheur est trouvé, le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est appelée pour rechercher l'accolade correspondante. Enfin, les deux accolades sont mis en surbrillance.  
  
 Bien que les accolades sont utilisés dans les noms de déclencheurs et d'analyser les raisons, ce processus n'est pas limité à accolades réelles. Toute paire de caractères qui est spécifié comme une correspondance paire est pris en charge. Exemples \(et\), \< et \>, et \[et\].  
  
 Supposons que le service de langage prend en charge les accolades correspondantes.  
  
1.  L'utilisateur tape une accolade fermante \(}\).  
  
2.  L'accolade est insérée au niveau du curseur dans le fichier source et le curseur est avancé par un.  
  
3.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée avec l'accolade fermante typé.  
  
4.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> des appels de méthode du <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton à la position juste avant la position actuelle du curseur. Ce jeton correspond à l'accolade fermante typé\).  
  
    1.  Le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> des appels de méthode du <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Colorizer> objet afin d'obtenir tous les jetons de la ligne actuelle.  
  
    2.  Le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> des appels de méthode du <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.IScanner> objet avec le texte de la ligne actuelle.  
  
    3.  Le <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> méthode appelle à plusieurs reprises la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.IScanner> objet pour rassembler tous les jetons de la ligne actuelle.  
  
    4.  Le <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> appelle une méthode privée la <xref:Microsoft.VisualStudio.Package.Source> classe pour obtenir le jeton qui contient la position voulue et passe dans la liste de jetons obtenus à partir de la <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> \(méthode\).  
  
5.  Le <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> méthode recherche un indicateur de déclencheur d'émission de jeton de <xref:Microsoft.VisualStudio.Package.TokenTriggers> sur le jeton qui est retourné à partir de la <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> méthode ; autrement dit, le jeton qui représente l'accolade fermante\).  
  
6.  Si le déclencheur indicateur de <xref:Microsoft.VisualStudio.Package.TokenTriggers> est trouvée, le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe est appelée.  
  
7.  Le <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> méthode démarre une opération d'analyse avec la valeur de motif de l'analyse de <xref:Microsoft.VisualStudio.Package.ParseReason>. Cette opération appelle finalement la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Si l'analyse asynchrone est activé, cet appel à la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode se produit sur un thread d'arrière\-plan.  
  
8.  Lorsque l'opération d'analyse est terminée, un gestionnaire d'achèvement interne \(également appelé une méthode de rappel\) nommé `HandleMatchBracesResponse` est appelée dans la <xref:Microsoft.VisualStudio.Package.Source> classe. Cet appel est effectué automatiquement par le <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base, pas par l'analyseur.  
  
9. Le `HandleMatchBracesResponse` méthode pour obtenir une liste d'étendues à partir de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet qui est stocké dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. \(Une balise span correspond un <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> structure qui spécifie une plage de lignes et de caractères dans le fichier source.\) Cette liste d'étendues contient généralement deux étendues, une pour les accolades ouvrantes et fermantes.  
  
10. Le `HandleBracesResponse` des appels de méthode le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> méthode sur le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objet qui est stocké dans le <xref:Microsoft.VisualStudio.Package.ParseRequest> objet. Cela met en évidence les étendues donnés.  
  
11. Si le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> est activé, le `HandleBracesResponse` méthode obtient le texte qui est englobé par l'étendue correspondante et affiche des 80 premiers caractères de cet intervalle dans la barre d'état. Il est préférable que le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode inclut l'élément de langage qui accompagne le couple. Pour plus d'informations, consultez la propriété <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Opération effectuée.  
  
### Résumé  
 L'opération d'accolades correspondantes est généralement limitée à simples paires d'éléments de langage. D'éléments plus complexes, telles que la correspondance des triplets \(»`if(…)`«, »`{`« et »`}`», ou «`else`«, »`{`« et »`}`»\), peut être mis en surbrillance dans le cadre d'une opération de saisie semi\-automatique des mots. Par exemple, lorsque le mot « else » est terminé, la mise en correspondance «`if`» instruction peut être mise en surbrillance. S'il existait une série de `if`\/`else if` toutes les instructions peuvent être mis en surbrillance à l'aide du même mécanisme que la correspondance des accolades. La <xref:Microsoft.VisualStudio.Package.Source> classe de base prend déjà en charge, comme suit : le moteur d'analyse doit retourner la valeur du déclencheur d'émission de jeton <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinée avec la valeur du déclencheur <xref:Microsoft.VisualStudio.Package.TokenTriggers> pour le jeton qui est antérieure à la position du curseur.  
  
 Pour plus d'informations, consultez [Accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## L'analyse de colorisation  
 Colorisation de code source est simple, uniquement identifier le type d'informations de couleur de jeton et de retour sur ce type. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe agit comme intermédiaire entre l'éditeur et le moteur d'analyse pour fournir des informations de couleur sur chaque jeton. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilise le <xref:Microsoft.VisualStudio.Package.IScanner> objet afin de colorisation d'une ligne et collecter des informations d'état pour toutes les lignes dans le fichier source. Dans les classes de service de langage MPF, la <xref:Microsoft.VisualStudio.Package.Colorizer> classe ne doit pas être remplacée car elle communique avec le moteur d'analyse uniquement via la <xref:Microsoft.VisualStudio.Package.IScanner> interface. Vous fournissez l'objet qui implémente le <xref:Microsoft.VisualStudio.Package.IScanner> interface en substituant la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode sur la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Le <xref:Microsoft.VisualStudio.Package.IScanner> Analyseur reçoit une ligne de code source via le <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> \(méthode\). Les appels à la <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> méthode sont répétées pour obtenir le jeton suivant dans la ligne jusqu'à épuisée de la ligne de jetons. La colorisation, le MPF traite tout le code source comme une séquence de lignes. Par conséquent, le moteur d'analyse doit être en mesure de faire face à la source en lui sous forme de lignes. En outre, n'importe quelle ligne peut être transmis à l'analyseur à tout moment, et la seule garantie est que l'analyseur reçoit la variable d'état de la ligne avant la ligne devant être analysés.  
  
 La <xref:Microsoft.VisualStudio.Package.Colorizer> classe est également utilisée pour identifier les déclencheurs d'émission de jeton. Ces déclencheurs indiquent le MPF qu'un jeton donné peut initier une opération plus complexe, tel que semi\-automatique ou accolades correspondantes. Identifier ces déclencheurs doive être rapide et doit se produire à n'importe quel emplacement, l'analyseur est mieux adapté pour cette tâche.  
  
 Pour plus d'informations, consultez [Coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## L'analyse de fonctionnalité et de portée  
 L'analyse de fonctionnalité et de portée nécessite plus d'efforts que seulement identifier les types de jetons sont rencontrées. L'analyseur a identifier le type de jeton, mais également les fonctionnalités pour laquelle le jeton est utilisé. Par exemple, un identificateur est simplement un nom, mais votre langage, un identificateur peut être le nom d'une classe, un espace de noms, une méthode ou une variable, en fonction du contexte. Le type général du jeton peut être un identificateur, mais l'identificateur peut\-être également les autres significations, selon qu'il est et où elle est définie. Cette identification requiert l'analyseur d'avoir connaissance approfondie de la langue en cours d'analyse. C'est là la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe arrive. La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe collecte des informations sur les identificateurs, méthodes, des paires de langage \(tels que des accolades et des parenthèses\) et langage triples \(similaire à des paires de langues, sauf qu'il existe trois parties, par exemple, «`foreach()`» »`{`« et »`}`»\). En outre, vous pouvez remplacer la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe pour prendre en charge l'identification du code, qui est utilisé dans la validation anticipée des points d'arrêt afin que le débogueur n'a pas à être chargé, et le **automatique** fenêtre de débogage, qui affiche les variables locales et les paramètres automatiquement lorsqu'un programme est débogué et requiert l'analyseur pour identifier des variables locales appropriées et les paramètres en plus de celles qui présente le débogueur.  
  
 Le <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est transmis à l'analyseur dans le cadre de la <xref:Microsoft.VisualStudio.Package.ParseRequest> objet et une nouvelle <xref:Microsoft.VisualStudio.Package.AuthoringSink> objet est créée chaque fois qu'un nouveau <xref:Microsoft.VisualStudio.Package.ParseRequest> objet est créé. En outre, la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode doit retourner un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet, qui est utilisée pour gérer diverses opérations IntelliSense. Le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet gère une liste de déclarations et une liste de méthodes, soit qui est remplie, selon la raison de l'analyse. La <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe doit être implémentée.  
  
## Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Vue d’ensemble du Service de langage ancien](../../extensibility/internals/legacy-language-service-overview.md)   
 [Coloration de syntaxe dans un Service de langage hérité](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Accolades correspondantes dans un Service de langage hérité](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)