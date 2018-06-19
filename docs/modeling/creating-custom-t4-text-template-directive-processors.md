---
title: Création de processeurs de directives de modèles de texte T4 personnalisés
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 49a3c24116e6cc78084d0830a662ad7a3522d32c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950590"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Création de processeurs de directives de modèles de texte T4 personnalisés

Le *processus de transformation de modèle de texte* prend un *modèle de texte* fichier comme entrée et produit un fichier texte comme sortie. Le *moteur de transformation de modèle de texte* le processus et le moteur interagit avec un hôte de transformation de modèle de texte et au moins un modèle de texte des contrôles *processeurs de directive* pour terminer le processus. Pour plus d’informations, consultez [le processus de Transformation de modèle de texte](../modeling/the-text-template-transformation-process.md).

Pour créer un processeur de directive personnalisé, vous devez définir une classe qui hérite de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou de <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

La différence entre ces deux est que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implémente l’interface minimale qui est nécessaire pour obtenir les paramètres de l’utilisateur et générer le code qui génère le fichier de sortie du modèle. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implémente le modèle de conception de requiert/fournit. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gère deux paramètres spéciaux, `requires` et `provides`.  Par exemple, un processeur de directive personnalisé peut accepter un nom de fichier à partir de l’utilisateur, ouvrir et lire le fichier et puis stocker le texte du fichier dans une variable nommée `fileText`. Une sous-classe de la <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> classe peut prendre un nom de fichier à partir de l’utilisateur en tant que la valeur de la `requires` paramètre et le nom de la variable dans laquelle stocker le texte en tant que la valeur de le `provides` paramètre. Ce processeur est ouvrir et lire le fichier et puis stocker le texte du fichier dans la variable spécifiée.

Avant d’appeler un processeur de directive personnalisé à partir d’un modèle de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devez l’inscrire.

Pour plus d’informations sur l’ajout de la clé de Registre, consultez [déploiement d’un processeur de Directive personnalisé](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Directives personnalisées

Une directive personnalisée se présente comme suit :

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Vous pouvez utiliser un processeur de directive personnalisé lorsque vous souhaitez accéder aux ressources ou données externes à partir d’un modèle de texte.

Différents modèles de texte peuvent partager les fonctionnalités fournies par un seul processeur de directive, afin de processeurs de directive permettent au code de facteur pour réutilisation. La fonction intégrée `include` directive est similaire, car vous pouvez l’utiliser pour factoriser du code et le partager entre différents modèles de texte. La différence est que toutes les fonctionnalités qui le `include` directive fournit est fixe et n’accepte pas les paramètres. Si vous souhaitez fournir des fonctionnalités communes à un modèle de texte et permettre de passer des paramètres, vous devez créer un processeur de directive personnalisé.

Quelques exemples de processeurs de directive personnalisés peuvent être :

-   Un processeur de directive pour retourner des données à partir d’une base de données qui accepte un nom d’utilisateur et un mot de passe en tant que paramètres.

-   Un processeur de directive pour ouvrir et lire un fichier qui accepte le nom du fichier en tant que paramètre.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Parties principales d’un processeur de directive personnalisé

Pour développer un processeur de directive, vous devez créer une classe qui hérite <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> ou <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Le plus important `DirectiveProcessor` méthodes que vous devez implémenter sont les suivantes.

-   `bool IsDirectiveSupported(string directiveName)` -Retour `true` si votre processeur de directive peut traiter la directive nommée.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Le moteur du modèle appelle cette méthode pour chaque occurrence d’une directive dans le modèle. Votre processeur doit enregistrer les résultats.

Une fois tous les appels à ProcessDirective() le moteur de création de modèles appelle ces méthodes :

-   `string[] GetReferencesForProcessingRun()` : Retourne les noms des assemblys que le code du modèle requiert.

-   `string[] GetImportsForProcessingRun()` : Retourne les espaces de noms qui peut être utilisé dans le code du modèle.

-   `string GetClassCodeForProcessingRun()` : Retourne le code des méthodes, propriétés et autres déclarations que le code du modèle peut utiliser. Pour ce faire, le plus simple consiste à générer une chaîne contenant le code c# ou Visual Basic. Pour rendre votre processeur de directive puisse être appelé à partir d’un modèle qui utilise n’importe quel langage CLR, vous pouvez construire les instructions sous forme d’arborescence CodeDom et puis retourner le résultat de la sérialisation de l’arborescence dans la langue utilisée par le modèle.

-   Pour plus d’informations, consultez [procédure pas à pas : création d’un processeur de Directive personnalisé](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Voir aussi

- [Déployer un processeur de Directive personnalisé](../modeling/deploying-a-custom-directive-processor.md) explique comment inscrire un processeur de directive personnalisé.
- [Procédure pas à pas : Création d’un processeur de Directive personnalisé](../modeling/walkthrough-creating-a-custom-directive-processor.md) décrit comment créer un processeur de directive personnalisé, comment enregistrer et tester le processeur de directive et comment mettre en forme le fichier de sortie au format HTML.