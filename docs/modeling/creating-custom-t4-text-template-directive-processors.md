---
title: "Creating Custom T4 Text Template Directive Processors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Creating Custom T4 Text Template Directive Processors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le *processus de transformation de modèle de texte* accepte un fichier *modèle de texte* comme entrée et produit un fichier texte comme sortie.  Le *moteur de transformation de modèle de texte* contrôle le processus ; il interagit avec un hôte de transformation de modèle de texte et un ou plusieurs *processeurs de directive* de modèle de texte pour exécuter le processus.  Pour plus d'informations, consultez [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Pour créer un processeur de directive personnalisé, vous devez définir une classe qui hérite de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou de <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 La différence entre ces deux classes réside dans le fait que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implémente l'interface minimale qui est nécessaire pour obtenir les paramètres de l'utilisateur et générer le code qui produit le fichier de sortie du modèle.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implémente le modèle de conception requires\/provides.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gère deux paramètres spéciaux, `requires` et `provides`.  Par exemple, un processeur de directive personnalisé peut accepter un nom de fichier fourni par l'utilisateur, ouvrir et lire le fichier, puis stocker le texte du fichier dans une variable nommée `fileText`.  Une sous\-classe de la classe <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> peut accepter un nom de fichier fourni par l'utilisateur comme valeur du paramètre `requires` et le nom de la variable dans laquelle le texte doit être stocké comme valeur du paramètre `provides`.  Ce processeur ouvrira et lira le fichier, puis stockera le texte qu'il contient dans la variable spécifiée.  
  
 Avant d'appeler un processeur de directive personnalisé à partir d'un modèle de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez l'inscrire.  
  
 Pour plus d'informations sur l'ajout de la clé de Registre, consultez [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md).  
  
## Directives personnalisées  
 Une directive personnalisée se présente comme suit :  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 Vous pouvez utiliser un processeur de directive personnalisé pour accéder à des ressources ou données externes à partir d'un modèle de texte.  
  
 Différents modèles de texte peuvent partager les fonctionnalités fournies par un même processeur de directive ; par conséquent, les processeurs de directive permettent de factoriser le code en vue de sa réutilisation.  La directive `include` intégrée est similaire car vous pouvez l'utiliser pour factoriser du code et le partager entre différents modèles de texte.  La différence réside dans le fait que toute fonctionnalité fournie par la directive `include` est fixe et n'accepte pas de paramètres.  Si vous voulez fournir des fonctionnalités communes à un modèle de texte et lui permettre de passer des paramètres, vous devez créer un processeur de directive personnalisé.  
  
 Voici des exemples de processeurs de directive personnalisés :  
  
-   Processeur de directive permettant de retourner les données d'une base de données ; il accepte un nom d'utilisateur et un mot de passe comme paramètres.  
  
-   Processeur de directive permettant d'ouvrir et de lire un fichier ; il accepte le nom du fichier comme paramètre.  
  
### Parties principales d'un processeur de directive personnalisé  
 Pour développer un processeur de directive, vous devez définir une classe qui hérite de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou de <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 Les méthodes `DirectiveProcessor` les plus importantes que vous devez implémenter sont les suivantes :  
  
-   `bool IsDirectiveSupported(string directiveName)` : retourne la valeur `true` si votre processeur de directive peut traiter la directive nommée.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` : le moteur du modèle appelle cette méthode pour chaque occurrence d'une directive dans le modèle.  Votre processeur doit enregistrer les résultats.  
  
 Une fois tous les appels à ProcessDirective\(\) effectués, le moteur de création de modèles appellera les méthodes suivantes :  
  
-   `string[] GetReferencesForProcessingRun()` : retourne les noms des assemblys que le code du modèle requiert.  
  
-   `string[] GetImportsForProcessingRun()` : retourne les espaces de noms qui peuvent être utilisés dans le code du modèle.  
  
-   `string GetClassCodeForProcessingRun()` : retourne le code des méthodes, des propriétés et d'autres déclarations que le code du modèle peut utiliser.  Le moyen le plus simple est de générer une chaîne contenant le code C\# ou Visual Basic.  Pour que votre processeur de directive puisse être appelé à partir d'un modèle utilisant n'importe quel langage CLR, vous pouvez construire les instructions sous la forme d'une arborescence CodeDom, puis retourner le résultat de la sérialisation de l'arborescence dans le langage utilisé par le modèle.  
  
-   Pour plus d'informations, consultez [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## Dans cette section  
 [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md)  
 Explique comment inscrire un processeur de directive personnalisé.  
  
 [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Indique comment créer un processeur de directive personnalisé, l'inscrire et le tester, puis mettre en forme le fichier de sortie au format HTML.