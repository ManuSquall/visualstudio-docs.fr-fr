---
title: "Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7765323944508eb0d739703bcb78dcf2cdfe08c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Valeurs par défaut VB, Projets, boîte de dialogue Options
Spécifie les paramètres par défaut pour les options de projet Visual Basic. Quand un projet est créé, les instructions d’options spécifiées sont ajoutées à l’en-tête du projet dans l’éditeur de code. Les options s’appliquent à tous les projets Visual Basic.  
  
 Pour accéder à cette boîte de dialogue, dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  
  
 **Option Explicit**  
 Définit la valeur par défaut du compilateur afin que les déclarations explicites des variables soient requises. Par défaut, **Option Explicit** a la valeur **On**. Pour plus d’informations, consultez [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Définit la valeur par défaut du compilateur afin que les conversions restrictives explicites soient requises et que les liaisons tardives soient interdites. Par défaut, **Option Strict** a la valeur **Off**. Pour plus d’informations, consultez [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Définit la valeur par défaut du compilateur pour les comparaisons de chaînes : Binary (respect de la casse) ou Text (non-respect de la casse). Par défaut, **Option Compare** a la valeur **Binary**. Pour plus d’informations, consultez [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Définit la valeur par défaut du compilateur pour l’inférence de type de variable locale. Par défaut, **Option Infer** a la valeur **On** pour les projets récemment créés et la valeur **Off** pour les projets migrés créés dans les versions antérieures de Visual Basic. Pour plus d’informations, consultez [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## <a name="see-also"></a>Voir aussi  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)