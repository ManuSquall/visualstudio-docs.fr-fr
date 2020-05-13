---
title: 'Zone d’essai 8 : Commutation plug-in Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704394"
---
# <a name="test-area-8-plug-in-switching"></a>Zone de test 8 : Commutation de plug-in
L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE) dispose de l’interface utilisateur (interface utilisateur) pour modifier le plug-in de contrôle source actuel. Cette zone de test fournit des cas de test pour le processus de sélection qui plug-in à utiliser pour le contrôle source de solution.

## <a name="command-menu-access"></a>Accès au menu de commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours de menu intégrés suivants sont utilisés dans les cas d’essai.

- Plug-in actuel de contrôle des sources : **Outils** -> **Options** -> **Source Control** -> **Plug-in Selection**.

- Changement de fixation de contrôle des sources: **File** -> **Source Control** -> **Change Source Control**...

## <a name="common-expected-behavior"></a>Comportement attendu commun
 Modifier le plug-in de contrôle source pour une solution est possible sans sortir Visual Studio ou recharger la solution. En outre, le plug-in de contrôle source actuel change automatiquement à celui utilisé par une solution lorsque cette solution est chargée.

## <a name="test-cases"></a>Cas de test
 Ce qui suit sont des cas de test spécifiques pour la zone de test de commutation plug-in.

### <a name="case-8a-automatic-change"></a>Cas 8a: Changement automatique

#### <a name="expected-behavior"></a>Comportement attendu
 Lorsqu’un utilisateur charge une solution sous contrôle source, la solution est automatiquement chargée et le plug-in de contrôle source approprié est sélectionné comme courant.

| Action | Étapes d’essai | Résultats attendus pour vérifier |
| - | - | - |
| Changement automatique de plug-in de contrôle de source | 1. Sélectionnez plug-in sous test en tant que courant **(Tools** -> **Options** -> **Source Control** -> **Plug-in Selection**.)<br />2. Créer un nouveau projet.<br />3. Ajouter la solution au contrôle des sources.<br />4. Sélectionnez un autre plug-in (par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5. Acceptez le déchargement de la solution prompte.<br />6. Rouvrir la solution à partir du disque. | La solution est ouverte.<br /><br /> Plug-in sous test est le plug-in de contrôle source actuel. |

### <a name="case-8b-solution-based-change"></a>Cas 8b : Changement basé sur la solution

#### <a name="expected-behavior"></a>Comportement attendu
 La solution peut faire modifier le plug-in de contrôle source associé.

| Action | Étapes d’essai | Résultats attendus pour vérifier |
|----------------------------------| - | - |
| Changement de plug-in pour une solution | 1. Sélectionnez plug-in sous test comme courant **(Tools** -> **Options** -> **Source Control** -> **Plug-in Selection**).<br />2. Créer un nouveau projet et une solution.<br />3. Ajouter la solution au contrôle des sources.<br />4. Débiné la solution à partir du contrôle des sources (à l’aide de la boîte de dialogue **De contrôle de source de changement).**<br />5. Sélectionnez un autre plug-in (par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6. Rechargez la solution à partir du disque s’il est déchargé.<br />7. Ajouter la solution au contrôle des sources.<br />8. Non relis la solution à partir du contrôle source (à l’aide de la boîte de dialogue **Change Source Control).**<br />9. Sélectionnez le plug-in à nouveau à l’essai.<br />10. Rechargez la solution à partir du disque s’il est déchargé.<br />11. Lier la solution à l’emplacement d’origine (à l’aide de la boîte de dialogue **De contrôle de source de changement).** | La solution est ajoutée au contrôle source en utilisant le plug-in sélectionné. |

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
