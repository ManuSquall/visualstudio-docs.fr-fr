---
title: Personnalisation d'une transformation de texte T4
description: Découvrez comment vous pouvez étendre le processus de transformation de modèle par défaut en personnalisant le processeur de directive de modèle de texte ou l’hôte de modèle de texte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35942b5f87458d1ccaf4892d33b5bba1dcdbb8a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389356"
---
# <a name="customize-t4-text-transformation"></a>Personnaliser une transformation de texte T4

Les modèles de texte sont une fonctionnalité de Visual Studio qui vous permet de générer du code de programme ou d’autres fichiers texte à l’aide d’un processus de transformation. À l’aide [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] de, vous pouvez étendre le processus de transformation de modèle par défaut en personnalisant le processeur de directive de modèle de texte ou l’hôte de modèle de texte.

## <a name="in-this-section"></a>Dans cette section

 [Processus de transformation du modèle de texte](../modeling/the-text-template-transformation-process.md) Décrit le fonctionnement de la transformation de texte et explique le rôle de l’hôte de modèle et des processeurs de directive.

 [Création de processeurs de directive de modèle de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md) Le processeur de directive traite les directives dans votre modèle, telles qu' `<#@template#>.` il s’exécute pendant la compilation du modèle, et peut charger des assemblys et d’autres ressources. Il peut également insérer du code qui chargera des ressources au moment de l’exécution. En définissant votre propre processeur de directive, vous pouvez réduire la complexité de vos modèles.

 [Appel d’une transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Si vous écrivez une extension Visual Studio telle qu’une commande de menu ou un gestionnaire d’événements, votre extension peut utiliser le service de création de modèles de texte pour transformer n’importe quel modèle de texte. Vous pouvez passer des données de paramètre dans le modèle à l’aide de l’objet de session et récupérer les valeurs à partir du modèle à l’aide de la `<#@parameter#>` directive.

 [Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md) Lorsque le code du modèle de texte s’exécute, l’hôte fournit l’accès aux fichiers externes et à l’état de l’application. Par exemple, l’hôte qui exécute des transformations de texte dans Visual Studio peut fournir l’accès à **Explorateur de solutions**. Il affiche également les erreurs dans la fenêtre de message d’erreur. Si vous souhaitez exécuter des transformations de texte dans un contexte différent, vous pouvez définir votre propre hôte qui fournit l’accès aux services disponibles dans ce contexte.

 Si vous écrivez une extension Visual Studio, envisagez d’utiliser le service de transformation de texte existant au lieu d’écrire votre propre hôte. Pour plus d’informations, consultez [appel de la transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Informations de référence

- L' [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md) fournit la syntaxe des directives et des blocs de contrôle de modèle de texte.
