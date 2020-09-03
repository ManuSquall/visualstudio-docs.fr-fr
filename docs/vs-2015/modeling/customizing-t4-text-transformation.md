---
title: Personnalisation de la transformation de texte T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654962"
---
# <a name="customizing-t4-text-transformation"></a>Personnalisation d'une transformation de texte T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles de texte sont une fonctionnalité de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui vous permet de générer du code de programme ou d’autres fichiers texte à l’aide d’un processus de transformation. À l’aide [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)] de, vous pouvez étendre le processus de transformation de modèle par défaut en personnalisant le processeur de directive de modèle de texte ou l’hôte de modèle de texte.

## <a name="in-this-section"></a>Dans cette section
 [Processus de transformation du modèle de texte](../modeling/the-text-template-transformation-process.md) Décrit le fonctionnement de la transformation de texte et explique le rôle de l’hôte de modèle et des processeurs de directive.

 [Création de processeurs de directive de modèle de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md) Le processeur de directive traite les directives dans votre modèle, telles qu' `<#@template#>.` il s’exécute pendant la compilation du modèle, et peut charger des assemblys et d’autres ressources. Il peut également insérer du code qui chargera des ressources au moment de l’exécution. En définissant votre propre processeur de directive, vous pouvez réduire la complexité de vos modèles.

 [Appel d’une transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Si vous écrivez une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension telle qu’une commande de menu ou un gestionnaire d’événements, votre extension peut utiliser le service de création de modèles de texte pour transformer n’importe quel modèle de texte. Vous pouvez passer des données de paramètre dans le modèle à l’aide de l’objet de session et récupérer les valeurs à partir du modèle à l’aide de la `<#@parameter#>` directive.

 [Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md) Lorsque le code du modèle de texte s’exécute, l’hôte fournit l’accès aux fichiers externes et à l’état de l’application. Par exemple, l’hôte qui exécute des transformations de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut fournir l’accès à l’Explorateur de solutions. Il affiche également les erreurs dans la fenêtre de message d’erreur. Si vous souhaitez exécuter des transformations de texte dans un contexte différent, vous pouvez définir votre propre hôte qui fournit l’accès aux services disponibles dans ce contexte.

 Si vous écrivez une [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extension, envisagez d’utiliser le service de transformation de texte existant au lieu d’écrire votre propre hôte. Pour plus d’informations, consultez [appel de la transformation de texte dans une extension vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Informations de référence
 [Écriture d'un modèle de texte T4](../modeling/writing-a-t4-text-template.md)

 Fournit la syntaxe des directives de modèle de texte et des blocs de contrôle.
