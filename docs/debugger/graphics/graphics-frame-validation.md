---
title: Validation des frames graphiques | Microsoft Docs
description: En savoir plus sur l’outil de validation de frame pour les graphiques dans Visual Studio. Cet outil affiche les erreurs et les avertissements associés à la liste des événements.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fe9b1ed3acbe588b342ba6550bc45558a2070d2
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727643"
---
# <a name="graphics-frame-validation"></a>Validation des frames graphiques
<!-- VERSIONLESS -->
Visual Studio 2017 et versions ultérieures prennent en charge l’outil de **validation de frame** .  La fenêtre validation de frame affiche les erreurs et les avertissements associés à la liste d’événements.  Pour afficher cette fenêtre, sélectionnez le menu **affichage > validation de frame** .

![Validation du frame](media/gfx_diag_frame_validation.png)

Cliquez sur le bouton **exécuter la validation** dans le coin supérieur gauche pour lancer l’analyse.  La réalisation de cette opération peut prendre plusieurs minutes en fonction de la complexité du cadre.  Les données qui s’affichent ici sont une combinaison de deux sources : les messages que D3D lui-même émet quand les [couches du SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) sont activées et les données collectées à partir du suivi de l’état interne de l’outil. Une fois l’opération terminée, plusieurs colonnes de données s’affichent :

| **Colonne** | **Description** |
|------------| - |
| ID d'événement | ID qui correspond à une entrée dans la fenêtre [liste des événements](graphics-event-list.md) . |
| Gravité | Endommagement, erreur, avertissement, information ou message. |
| Category | Application définie, divers, initialisation, nettoyage, compilation, création d’État, paramètre d’État, obtention d’État, exécution, manipulation de ressources, nuanceur, redondant et inutilisé. |
| Message | Message associé à l'événement. |
| Événement | Événement associé à l’erreur ou à l’avertissement. |

## <a name="see-also"></a>Voir aussi
[Graphics Diagnostics (débogage DirectX Graphics)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->