---
title: Création de processeurs de directive de modèle de texte T4 personnalisés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eef9fd14dc78ff1f377ffb94bcf76fde0c401783
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651217"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Création de processeurs de directives de modèles de texte T4 personnalisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le *processus de transformation de modèle de texte* utilise un fichier de *modèle de texte* comme entrée et produit un fichier texte comme sortie. Le *moteur de transformation de modèle de texte* contrôle le processus et le moteur interagit avec un hôte de transformation de modèle de texte et un ou plusieurs *processeurs de directive* de modèle de texte pour terminer le processus. Pour plus d’informations, consultez [processus de transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).

 Pour créer un processeur de directive personnalisé, vous devez définir une classe qui hérite de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou de <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

 La différence entre ces deux est que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implémente l’interface minimale nécessaire pour obtenir des paramètres de l’utilisateur et générer le code qui produit le fichier de sortie du modèle. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implémente le modèle de conception requires/fournit. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gère deux paramètres spéciaux, `requires` et `provides`.  Par exemple, un processeur de directive personnalisé peut accepter un nom de fichier de l’utilisateur, ouvrir et lire le fichier, puis stocker le texte du fichier dans une variable nommée `fileText`. Une sous-classe de la classe <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> peut accepter un nom de fichier de l’utilisateur comme valeur du paramètre `requires` et le nom de la variable dans laquelle le texte doit être stocké comme valeur du paramètre `provides`. Ce processeur ouvre et lit le fichier, puis stocke le texte du fichier dans la variable spécifiée.

 Avant d’appeler un processeur de directive personnalisé à partir d’un modèle de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vous devez l’inscrire.

 Pour plus d’informations sur l’ajout de la clé de Registre, consultez [déploiement d’un processeur de directive personnalisé](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Directives personnalisées
 Une directive personnalisée se présente comme suit :

 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`

 Vous pouvez utiliser un processeur de directive personnalisé lorsque vous souhaitez accéder à des données ou des ressources externes à partir d’un modèle de texte.

 Différents modèles de texte peuvent partager les fonctionnalités fournies par un processeur de directive unique, de sorte que les processeurs de directive offrent un moyen de factoriser le code en vue de sa réutilisation. La directive `include` intégrée est similaire, car vous pouvez l’utiliser pour factoriser le code et le partager entre différents modèles de texte. La différence réside dans le fait que toutes les fonctionnalités fournies par la directive `include` sont fixes et n’acceptent pas de paramètres. Si vous souhaitez fournir des fonctionnalités communes à un modèle de texte et autoriser le modèle à passer des paramètres, vous devez créer un processeur de directive personnalisé.

 Voici quelques exemples de processeurs de directive personnalisés :

- Processeur de directive pour retourner des données d’une base de données qui accepte un nom d’utilisateur et un mot de passe en tant que paramètres.

- Processeur de directive permettant d’ouvrir et de lire un fichier qui accepte le nom du fichier en tant que paramètre.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Parties principales d’un processeur de directive personnalisé
 Pour développer un processeur de directive, vous devez créer une classe qui hérite de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

 Les méthodes `DirectiveProcessor` les plus importantes que vous devez implémenter sont les suivantes.

- `bool IsDirectiveSupported(string directiveName)`-retourne `true` si votre processeur de directive peut gérer la directive nommée.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`-le moteur de modèle appelle cette méthode pour chaque occurrence d’une directive dans le modèle. Votre processeur doit enregistrer les résultats.

  Après tous les appels à ProcessDirective (), le moteur de création de modèles appellera les méthodes suivantes :

- `string[] GetReferencesForProcessingRun()`-retourne les noms des assemblys requis par le code du modèle.

- `string[] GetImportsForProcessingRun()`-retourne les espaces de noms qui peuvent être utilisés dans le code du modèle.

- `string GetClassCodeForProcessingRun()`-retourne le code des méthodes, des propriétés et d’autres déclarations que le code du modèle peut utiliser. Le moyen le plus simple consiste à créer une chaîne contenant le C# code ou Visual Basic. Pour que votre processeur de directive puisse être appelé à partir d’un modèle qui utilise n’importe quel langage CLR, vous pouvez construire les instructions sous la forme d’une arborescence CodeDom, puis retourner le résultat de la sérialisation de l’arborescence dans le langage utilisé par le modèle.

- Pour plus d’informations, consultez [procédure pas à pas : création d’un processeur de directive personnalisé](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="in-this-section"></a>Dans cette section
 [Déploiement d’un processeur de directive personnalisé](../modeling/deploying-a-custom-directive-processor.md) Explique comment inscrire un processeur de directive personnalisé.

 [Procédure pas à pas : création d’un processeur de directive personnalisé](../modeling/walkthrough-creating-a-custom-directive-processor.md) Décrit comment créer un processeur de directive personnalisé, comment inscrire et tester le processeur de directive, et comment mettre en forme le fichier de sortie au format HTML.
