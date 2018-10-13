---
title: Personnalisation d’une Transformation de texte T4 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dc44c1de2e0a590b73916a8496a7fe5cae7cb07e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200237"
---
# <a name="customizing-t4-text-transformation"></a>Personnalisation d'une transformation de texte T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modèles de texte sont une fonctionnalité de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vous permettent de générer du code de programme ou d’autres fichiers texte via un processus de transformation. À l’aide de [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], vous pouvez étendre le processus de transformation de modèle par défaut en personnalisant le processeur de directive de modèle de texte ou l’hôte de modèle de texte.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Processus de transformation du modèle de texte](../modeling/the-text-template-transformation-process.md)  
 Décrit le fonctionne de la transformation de texte et explique le rôle de l’hôte de modèle et les processeurs de directive.  
  
 [Création de processeurs de directives de modèles de texte T4 personnalisés](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Le processeur de directive traite tels que les directives dans votre modèle, `<#@template#>.` s’exécute pendant la compilation du modèle, elle peut charger des assemblys et autres ressources. Il peut également insérer le code qui charge les ressources lors de l’exécution. En définissant votre propre processeur de directive, vous pouvez réduire la complexité de vos modèles.  
  
 [Appel d’une transformation de texte dans une extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Si vous écrivez un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension tel qu’un gestionnaire de commande ou un événement menu, les votre extension peut utiliser le Service de création de modèles de texte pour transformer n’importe quel modèle de texte. Vous pouvez passer des données de paramètre dans le modèle à l’aide de l’objet de Session et obtenir les valeurs dans le modèle à l’aide de la `<#@parameter#>` directive.  
  
 [Traitement des modèles de texte à l’aide d’un hôte personnalisé](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Lorsque le code du modèle de texte s’exécute, l’hôte fournit l’accès aux fichiers externes et l’état de l’application. Par exemple, l’hôte qui exécute les transformations de texte dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut fournir l’accès à l’Explorateur de solutions. Il affiche également les erreurs dans la fenêtre de message d’erreur. Si vous souhaitez exécuter des transformations de texte dans un contexte différent, vous pouvez définir votre propre hôte qui fournit l’accès aux services disponibles dans ce contexte.  
  
 Si vous écrivez un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension, envisagez d’utiliser le service de transformation de texte existant au lieu d’écrire votre propre hôte. Pour plus d’informations, consultez [appel d’une Transformation de texte dans une Extension VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Référence  
 [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)  
  
 Fournit la syntaxe des directives de modèles de texte et les blocs de contrôle.



