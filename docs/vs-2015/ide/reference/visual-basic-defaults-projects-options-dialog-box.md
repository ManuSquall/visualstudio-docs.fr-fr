---
title: Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3370ecc8a80014f9d80152713140de7731bac058
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493537"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Valeurs par défaut VB, Projets, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [paramètres par défaut de Visual Basic, projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box).  
  
  
Spécifie les paramètres par défaut pour les options de projet Visual Basic. Quand un projet est créé, les instructions d’options spécifiées sont ajoutées à l’en-tête du projet dans l’éditeur de code. Les options s’appliquent à tous les projets Visual Basic.  
  
 Pour accéder à cette boîte de dialogue, dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  
  
 **Option Explicit**  
 Définit la valeur par défaut du compilateur afin que les déclarations explicites des variables soient requises. Par défaut, **Option Explicit** a la valeur **On**. Pour plus d’informations, consultez [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).  
  
 **Option Strict**  
 Définit la valeur par défaut du compilateur afin que les conversions restrictives explicites soient requises et que les liaisons tardives soient interdites. Par défaut, **Option Strict** a la valeur **Off**. Pour plus d’informations, consultez [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da).  
  
 **Option Compare**  
 Définit la valeur par défaut du compilateur pour les comparaisons de chaînes : Binary (respect de la casse) ou Text (non-respect de la casse). Par défaut, **Option Compare** a la valeur **Binary**. Pour plus d’informations, consultez [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).  
  
 **Option Infer**  
 Définit la valeur par défaut du compilateur pour l’inférence de type de variable locale. Par défaut, **Option Infer** a la valeur **On** pour les projets récemment créés et la valeur **Off** pour les projets migrés créés dans les versions antérieures de Visual Basic. Pour plus d’informations, consultez [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).  
  
## <a name="see-also"></a>Voir aussi  
 [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)


