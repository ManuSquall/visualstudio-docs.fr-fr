---
title: Validation du Frame Graphics | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fee7e1db2716c2c7fedba41970ccfb0471e3d230
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511293"
---
# <a name="graphics-frame-validation"></a>Validation du Frame Graphics
<!-- VERSIONLESS --> Visual Studio 2017 et une prise en charge la **Validation du Frame** outil.  La fenêtre de Validation du Frame affiche les erreurs et avertissements associés à la liste des événements.  Pour afficher cette fenêtre, sélectionnez le **Afficher > Validation du Frame** menu.

![Validation du frame](media/gfx_diag_frame_validation.png)

Cliquez sur le **exécuter la Validation** bouton dans l’angle supérieur gauche pour lancer l’analyse.  Il peut prendre plusieurs minutes selon la complexité du frame.  Les données qui s’affiche ici est une combinaison de deux sources : les messages que D3D lui-même émet lorsque [couches SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) est activé et les données collectées à partir de l’état interne de l’outil de suivi. Une fois terminé, vous verrez plusieurs colonnes de données :

**Colonne**|**Description**
---|---
ID d'événement | ID qui est mappé à une entrée dans le [liste des événements](graphics-event-list.md) fenêtre.
Gravité | Endommagement, erreur, avertissement, informations ou Message.
Category | Application définie et divers, l’initialisation, nettoyage, Compilation, création de l’état, paramètre d’état, obtention de l’état, l’exécution, Manipulation des ressources, nuanceur, redondante ou inutilisée.
Message | Le message associé à l’événement.
Événement | L’événement associé à l’erreur ou l’avertissement.

## <a name="see-also"></a>Voir aussi  
[Graphics Diagnostics (débogage DirectX Graphics)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->