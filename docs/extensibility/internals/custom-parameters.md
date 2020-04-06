---
title: Paramètres personnalisés (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708948"
---
# <a name="custom-parameters"></a>Paramètres personnalisés
Les paramètres personnalisés contrôlent le fonctionnement d’un sorcier après le début d’un assistant. Un fichier *.vsz* connexe fournit un tableau de paramètres définis par l’utilisateur qui sont emballés par l’environnement de développement intégré (IDE) et transmis à l’assistant comme un tableau de cordes lorsque l’assistant est commencé. L’assistant analyse alors la gamme de cordes et utilise l’information pour contrôler le fonctionnement réel de l’assistant. De cette façon, un assistant peut personnaliser la fonctionnalité en fonction du contenu du fichier *.vsz.*

 Les paramètres de contexte, d’autre part, définissent l’état du projet lorsque l’assistant est lancé. Pour plus d’informations, voir [Paramètres Context](../../extensibility/internals/context-parameters.md).

 Voici un exemple d’un fichier *.vsz* qui a des paramètres personnalisés:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 L’auteur du fichier *.vsz* ajoute les valeurs des paramètres. Lorsqu’un utilisateur sélectionne **un nouveau projet** ou ajoutez un nouvel **élément** sur le menu **Fichier** ou en cliquant à droite sur un projet dans **Solution Explorer,** l’IDE recueille ces valeurs dans un tableau de cordes. L’IDE appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> la méthode <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> du projet avec l’ensemble du drapeau, et le projet appelle la <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> méthode qui est responsable de l’exécution de l’assistant et le retour du résultat.

 L’assistant est responsable d’analyser la gamme de cordes et d’agir sur les cordes de manière appropriée. De cette manière, en implémentant des paramètres personnalisés, vous pouvez créer un assistant qui remplit une variété de fonctions. En d’autres termes, un assistant pourrait avoir trois fichiers *.vsz* différents. Chaque fichier passe différents ensembles de paramètres personnalisés pour contrôler le comportement de l’assistant dans diverses situations.

 Pour plus d’informations, voir [le fichier Wizard (.vsz).](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Paramètres de contexte](../../extensibility/internals/context-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichier Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
