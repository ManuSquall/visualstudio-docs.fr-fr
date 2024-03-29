---
title: Paramètres personnalisés | Microsoft Docs
description: Découvrez comment créer des paramètres personnalisés qui contrôlent le fonctionnement d’un Assistant après le démarrage d’un Assistant, en modifiant un fichier. vsz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e5d8d9bf78f06dd55a88a2fbd47749224be3949
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091095"
---
# <a name="custom-parameters"></a>Paramètres personnalisés
Les paramètres personnalisés contrôlent l’opération d’un Assistant après le démarrage d’un Assistant. Un fichier *. vsz* associé fournit un tableau de paramètres définis par l’utilisateur qui sont empaquetés par l’environnement de développement intégré (IDE) et transmis à l’Assistant sous la forme d’un tableau de chaînes au démarrage de l’Assistant. L’Assistant analyse ensuite le tableau de chaînes et utilise les informations pour contrôler le fonctionnement réel de l’Assistant. De cette manière, un Assistant peut personnaliser les fonctionnalités en fonction du contenu du fichier *. vsz* .

 En revanche, les paramètres de contexte définissent l’état du projet au démarrage de l’Assistant. Pour plus d’informations, consultez [paramètres de contexte](../../extensibility/internals/context-parameters.md).

 Voici un exemple de fichier *. vsz* qui a des paramètres personnalisés :

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 L’auteur du fichier *. vsz* ajoute les valeurs des paramètres. Quand un utilisateur sélectionne **nouveau projet** ou **ajoute un nouvel élément** dans le menu **fichier** ou en cliquant avec le bouton droit sur un projet dans **Explorateur de solutions**, l’IDE collecte ces valeurs dans un tableau de chaînes. L’IDE appelle ensuite la méthode du projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> avec l' <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> indicateur défini, et le projet appelle la <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> méthode qui est chargée d’exécuter l’Assistant et de retourner le résultat.

 L’Assistant est chargé d’analyser le tableau de chaînes et d’agir correctement sur les chaînes. De cette manière, en implémentant des paramètres personnalisés, vous pouvez créer un assistant qui exécute diverses fonctions. En d’autres termes, un Assistant peut avoir trois fichiers *. vsz* différents. Chaque fichier passe différents jeux de paramètres personnalisés pour contrôler le comportement de l’Assistant dans différentes situations.

 Pour plus d’informations, consultez [fichier Assistant (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Assistant (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
