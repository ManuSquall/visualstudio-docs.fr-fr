---
title: Valeurs par défaut VB, Projets, boîte de dialogue Options
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d211b69a4fb8ce988298a39310f103574b563721
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
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

- [Projets et solutions](../../ide/solutions-and-projects-in-visual-studio.md)