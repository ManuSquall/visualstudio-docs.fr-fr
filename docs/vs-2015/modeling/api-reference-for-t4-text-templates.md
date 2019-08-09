---
title: Informations de référence sur les API pour les modèles de texte T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 63279da9-69ac-49ad-ac7d-43957c45e0ce
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 00be275fe36fd453fd3bd1f6bcf5c0911f7bb380
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871895"
---
# <a name="api-reference-for-t4-text-templates"></a>Référence API pour les modèles de texte T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’API de création de modèles de texte vous permet d’appeler et de personnaliser la transformation des [modèles de texte](../modeling/code-generation-and-t4-text-templates.md).

## <a name="namespaces"></a>Espaces de noms

|Espace de noms|Objectif|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.TextTemplating>|Contient des classes pour la fonctionnalité de transformation de modèle de texte. Le moteur de transformation de modèle de texte est intégré à Visual Studio et transforme les fichiers de modèle de texte en fichiers de sortie texte générés.|
|[Modélisation](/previous-versions/ee844312(v=vs.140))|Fournit des fonctionnalités de transformation de texte liées aux modèles UML et aux langages spécifiques à un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] domaine, tels que l’accès à ModelBus.|
|<xref:Microsoft.VisualStudio.TextTemplating.VSHost>|Fournit l’accès au service de création de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]modèles de texte dans.|
