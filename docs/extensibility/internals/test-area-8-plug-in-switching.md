---
title: 'Test zone 8 : Basculement du plug-in | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 534bd9338181c5b682779b62a9c118a5ccaf8cda
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-8-plug-in-switching"></a>Test zone 8 : Basculement du plug-in
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’environnement de développement intégré (IDE) est l’interface utilisateur (IU) pour modifier le plug-in du contrôle de source actuel. Cette zone de test fournit des cas de test pour le processus de sélection du plug-in à utiliser pour le contrôle de source de solution qui.  
  
## <a name="command-menu-access"></a>Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
-   Plug-in de contrôle de code source en cours : **outils** -> **Options** -> **contrôle de code Source** -> **sélection du plug-in** .  
  
-   Modifier la source de liaison de contrôle : **fichier** -> **contrôle de code Source** -> **modifier le contrôle de code Source**...  
  
## <a name="common-expected-behavior"></a>Comportement attendu commun  
 Il est possible de modifier le plug-in pour une solution de contrôle de code source sans quitter Visual Studio ou de recharger la solution. En outre, le plug-in du contrôle de source actuel change automatiquement de celui utilisé par une solution quand cette solution est chargée.  
  
## <a name="test-cases"></a>Cas de test  
 Voici les cas de test spécifiques pour la zone de test de commutation plug-in.  
  
### <a name="case-8a-automatic-change"></a>Cas 8 a : modification automatique  
  
#### <a name="expected-behavior"></a>Comportement attendu  
 Lorsqu’un utilisateur charge une solution sous contrôle de code source, la solution est automatiquement chargée et le plug-in de contrôle de source approprié est sélectionné comme en cours.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Modification de plug-in de contrôle de source automatique|1.  Sélectionnez plug-in sous test en cours (**outils** -> **Options** -> **contrôle de code Source** -> **plug-in Sélection**.)<br />2.  Créer un nouveau projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Sélectionnez un autre plug-in (par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Acceptez déchargement solution.<br />6.  Rouvrez la solution à partir du disque.|Solution est ouverte.<br /><br /> Plug-in de test est le plug-in du contrôle de source actuel.|  
  
### <a name="case-8b-solution-based-change"></a>Cas 8 b : basée sur une Solution de modification  
  
#### <a name="expected-behavior"></a>Comportement attendu  
 La solution peut avoir ses plug-in de contrôle de code source associé modifié.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Modification de plug-in pour une solution|1.  Sélectionnez plug-in sous test en cours (**outils** -> **Options** -> **contrôle de code Source** -> **plug-in Sélection**).<br />2.  Créer une solution et un nouveau projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Déconnectez la solution de contrôle de code source (à l’aide de la **modifier le contrôle de code Source** boîte de dialogue).<br />5.  Sélectionnez un autre plug-in (par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Recharger la solution à partir du disque de déchargement.<br />7.  Ajouter la solution au contrôle de code source.<br />8.  Déconnectez la solution de contrôle de code source (à l’aide de **modifier le contrôle de code Source** boîte de dialogue).<br />9. Sélectionnez le plug-in de test à nouveau.<br />10. Recharger la solution à partir du disque de déchargement.<br />11. Lier la solution à l’emplacement d’origine (à l’aide de la **modifier le contrôle de code Source** boîte de dialogue).|Solution est ajoutée au contrôle de code source à l’aide du plug-in.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)