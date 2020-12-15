---
title: 'Zone de test 8 : commutation de plug-in | Microsoft Docs'
description: Cette zone de test de contrôle de code source fournit des cas de test pour le processus de sélection du plug-in à utiliser pour le contrôle de code source de la solution dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b6c3a25aa9312073d3ce4a60752d41585fcee7b3
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487645"
---
# <a name="test-area-8-plug-in-switching"></a>Zone de test 8 : Commutation de plug-in
L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement de développement intégré (IDE) dispose de l’interface utilisateur pour modifier le plug-in de contrôle de code source actuel. Cette zone de test fournit des cas de test pour le processus de sélection du plug-in à utiliser pour le contrôle de code source de la solution.

## <a name="command-menu-access"></a>Accès au menu commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chemins d’accès au menu de l’environnement de développement intégré suivants sont utilisés dans les cas de test.

- Plug-in de contrôle de code source actuel : **Outils**  ->  **options**  ->    ->  **sélection du plug-in de contrôle de** code source.

- Modifier la liaison de contrôle de code source : contrôle de source de **fichier**  ->    ->  **modifier le contrôle** de code source...

## <a name="common-expected-behavior"></a>Comportement attendu courant
 La modification du plug-in de contrôle de code source pour une solution est possible sans quitter Visual Studio ou recharger la solution. En outre, le plug-in de contrôle de code source actuel devient automatiquement celui utilisé par une solution lorsque cette solution est chargée.

## <a name="test-cases"></a>Cas de test
 Les éléments suivants sont des cas de test spécifiques pour la zone de test de basculement de plug-in.

### <a name="case-8a-automatic-change"></a>Cas 8A : modification automatique

#### <a name="expected-behavior"></a>Comportement attendu
 Lorsqu’un utilisateur charge une solution sous contrôle de code source, la solution est automatiquement chargée et le plug-in de contrôle de code source approprié est sélectionné comme étant en cours.

| Action | Étapes de test | Résultats attendus à vérifier |
| - | - | - |
| Modification du plug-in de contrôle de code source automatique | 1. Sélectionnez le plug-in sous test en tant que actuel (**Outils**  ->  **options**  ->    ->  **sélection du plug-in de contrôle de** code source.)<br />2. Créez un nouveau projet.<br />3. Ajoutez la solution au contrôle de code source.<br />4. Sélectionnez un autre plug-in (par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />5. acceptez l’invite de déchargement de la solution.<br />6. rouvrez la solution à partir du disque. | La solution est ouverte.<br /><br /> Le plug-in testé est le plug-in de contrôle de code source actuel. |

### <a name="case-8b-solution-based-change"></a>Cas 8B : modification basée sur la solution

#### <a name="expected-behavior"></a>Comportement attendu
 Le plug-in du contrôle de code source associé à la solution peut être modifié.

| Action | Étapes de test | Résultats attendus à vérifier |
|----------------------------------| - | - |
| Modification du plug-in pour une solution | 1. Sélectionnez le plug-in sous test en tant que actuel (**Outils**  ->  **options**  ->    ->  **sélection du plug-in de contrôle de** code source).<br />2. Créez un projet et une solution.<br />3. Ajoutez la solution au contrôle de code source.<br />4. dissociez la solution du contrôle de code source (à l’aide de la boîte de dialogue **modifier le contrôle de code source** ).<br />5. Sélectionnez un autre plug-in (par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />6. Rechargez la solution à partir du disque si elle est déchargée.<br />7. Ajoutez la solution au contrôle de code source.<br />8. dissociez la solution du contrôle de code source (à l’aide de la boîte de dialogue **modifier le contrôle de code source** ).<br />9. Sélectionnez le plug-in sous test.<br />10. recharger la solution à partir du disque si elle est déchargée.<br />11. liez la solution à l’emplacement d’origine (à l’aide de la boîte de dialogue **modifier le contrôle de code source** ). | La solution est ajoutée au contrôle de code source à l’aide du plug-in sélectionné. |

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
