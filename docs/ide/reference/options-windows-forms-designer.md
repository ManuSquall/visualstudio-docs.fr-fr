---
title: Options, Concepteur Windows Forms, Général
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2a72b27dc2277501d0e0957c8b89b551f4d6852d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568059"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Boîte de dialogue Options : Concepteur Windows Forms

La page d’options du Concepteur Windows Forms vous permet de définir des préférences pour les grilles et d’autres fonctionnalités du Concepteur Windows Forms dans Visual Studio. Ouvrez la boîte de dialogue **Options** à partir du menu **Outils**.

## <a name="code-generation-settings"></a>Paramètres de génération de code

**Génération de code optimisé**\
Active la génération de code optimisé. Certains contrôles peuvent ne pas être compatibles avec ce mode. Pour que cette modification prenne effet, Visual Studio doit être fermé et rouvert.

## <a name="high-dpi-support"></a>Prise en charge de la haute résolution

**Notifications de mise à l'échelle PPP**\
Affichez un message dans le Concepteur Windows Form qui peut redémarrer Visual Studio avec une mise à l’échelle de 100 %. Pour plus d’informations, consultez [Désactiver la reconnaissance DPI dans Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Paramètres de disposition

**Taille de cellule de grille par défaut**\
Définit l’espacement, en pixels, entre le quadrillage horizontal et le quadrillage vertical sur le concepteur. La taille par défaut est 8, 8. La taille maximale est 200, 200.

**Mode disposition**\
Spécifie le système d’alignement à utiliser pour la disposition. Vous pouvez choisir SnapToGrid ou SnapLines.

**Afficher la grille**\
Spécifie si les concepteurs affichent la grille de dimensionnement. Par défaut, la grille est activée.

**Aligner sur la grille**\
Détermine si les concepteurs doivent aligner les objets et les contrôles sur la grille. En d’autres termes, le redimensionnement et le déplacement des éléments sur le concepteur sont limités à l’incrément GridSize quand cette fonctionnalité est activée. Si SnapToGrid est activé, il est plus facile d’aligner avec précision les différents aspects de l’interface utilisateur, mais cela limite la liberté de placement des contrôles. Par défaut, SnapToGrid est activé.

## <a name="object-bound-smart-tag-settings"></a>Paramètres des balises actives liées à un objet

**Ouvrir automatiquement les balises actives**\
Détermine si les contrôles et les composants affichent des balises actives. Les contrôles et les composants ne prennent pas tous en charge les balises actives.

## <a name="refactoring"></a>Refactoring

**Activer la refactorisation lors du changement de nom**\
Lorsque la valeur est `true`, une opération de refactorisation de changement de nom est effectuée lorsque vous renommez un composant à partir de la fenêtre Propriétés ou de la fenêtre Structure du document.

## <a name="toolbox"></a>Boîte à outils

**Remplir automatiquement la boîte à outils**\
Détermine si la fenêtre Boîte à outils est automatiquement remplie avec les composants et les contrôles générés par le projet.
