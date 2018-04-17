---
title: Personnalisation d’une Transformation de texte T4 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 158e39dfe01dd0016d622918082d6ec4874dc661
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-t4-text-transformation"></a>Personnalisation d'une transformation de texte T4
Modèles de texte sont une fonctionnalité de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permettent de générer du code de programme ou d’autres fichiers texte via un processus de transformation. À l’aide de [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], vous pouvez étendre le processus de transformation de modèle par défaut en personnalisant le processeur de directive de modèle de texte ou l’hôte de modèle de texte.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Processus de transformation du modèle de texte](../modeling/the-text-template-transformation-process.md)  
 Décrit le fonctionne de la transformation de texte et explique le rôle de l’hôte de modèle et les processeurs de directive.  
  
 [Création de processeurs de directives de modèles de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Le processeur de directive traite les directives de votre modèle, telles que `<#@template#>.` il s’exécute lors de la compilation du modèle et peut charger des assemblys et autres ressources. Il peut également insérer du code qui charge les ressources lors de l’exécution. En définissant votre propre processeur de directive, vous pouvez réduire la complexité de vos modèles.  
  
 [Appel d’une transformation de texte dans une extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Si vous écrivez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensions, telles que d’un gestionnaire d’événement ou de la commande de menu, votre extension peut utiliser le Service de création de modèles de texte pour transformer n’importe quel modèle de texte. Vous pouvez passer des données de paramètre dans le modèle à l’aide de l’objet de Session et obtenir les valeurs dans le modèle à l’aide de la `<#@parameter#>` la directive.  
  
 [Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Lorsque le code du modèle de texte s’exécute, l’hôte fournit l’accès aux fichiers externes et l’état de l’application. Par exemple, l’hôte qui exécute les transformations de texte dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permettent d’accéder à l’Explorateur de solutions. Il affiche également les erreurs dans la fenêtre de message d’erreur. Si vous souhaitez exécuter des transformations de texte dans un contexte différent, vous pouvez définir votre propre hôte qui permet d’accéder aux services disponibles dans ce contexte.  
  
 Si vous écrivez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension, envisagez d’utiliser le service de transformation de texte existant au lieu d’écrire votre propre hôte. Pour plus d’informations, consultez [appeler la Transformation de texte dans une Extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Référence  
 [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)  
  
 Fournit la syntaxe des directives de modèle de texte et les blocs de contrôle.