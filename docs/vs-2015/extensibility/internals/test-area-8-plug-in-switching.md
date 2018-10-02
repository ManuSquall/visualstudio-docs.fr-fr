---
title: 'Zone de test 8 : Plug-in commutation | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6633c2bd2f2f968f10aef215f395203f95c99da1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504692"
---
# <a name="test-area-8-plug-in-switching"></a>Zone de test 8 : Commutation de plug-in
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Test zone 8 : commutation de plug-in](https://docs.microsoft.com/visualstudio/extensibility/internals/test-area-8-plug-in-switching).  
  
Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE) a l’interface utilisateur (IU) pour modifier le plug-in du contrôle de source en cours. Cette zone de test fournit un cas de test pour le processus de sélection du plug-in à utiliser pour le contrôle de code source de solution qui.  
  
## <a name="command-menu-access"></a>Accès au Menu de commande  
 Ce qui suit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
-   Plug-in de contrôle de code source en cours : **outils** -> **Options** -> **contrôle de code Source** -> **sélection du plug-in** .  
  
-   Modifier la source de liaison de contrôle : **fichier** -> **contrôle de code Source** -> **modifier le contrôle de Source**...  
  
## <a name="common-expected-behavior"></a>Comportement attendu commun  
 Il est possible de modifier le plug-in pour une solution de contrôle de code source sans quitter Visual Studio ou de recharger la solution. En outre, le plug-in de contrôle source actuel change automatiquement celle utilisée par une solution quand cette solution est chargée.  
  
## <a name="test-cases"></a>Cas de test  
 Voici les cas de test spécifiques pour la zone de test de basculement plug-in.  
  
### <a name="case-8a-automatic-change"></a>Cas 8 a : modification automatique  
  
#### <a name="expected-behavior"></a>Comportement attendu  
 Lorsqu’un utilisateur charge une solution qui est sous contrôle de code source, la solution est automatiquement chargée et le plug-in de contrôle de code source approprié est sélectionné comme en cours.  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Modification de plug-in de contrôle de source automatique|1.  Sélectionnez plug-in sous test autant à jour (**outils** -> **Options** -> **contrôle de code Source** -> **plug-in Sélection**.)<br />2.  Créer un nouveau projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Sélectionner un autre plug-in (par exemple, [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />5.  Accepter l’invite déchargement de solution.<br />6.  Rouvrez la solution à partir du disque.|Solution est ouverte.<br /><br /> Plug-in de test est le plug-in du contrôle de source en cours.|  
  
### <a name="case-8b-solution-based-change"></a>Cas 8 b : modification sur les solutions  
  
#### <a name="expected-behavior"></a>Comportement attendu  
 La solution peut avoir son plug-in de contrôle de code source associé modifié.  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Modification de plug-in pour une solution|1.  Sélectionnez plug-in sous test autant à jour (**outils** -> **Options** -> **contrôle de code Source** -> **plug-in Sélection**).<br />2.  Créer un nouveau projet et solution.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Déconnectez la solution de contrôle de code source (à l’aide de la **modifier le contrôle de Source** boîte de dialogue).<br />5.  Sélectionner un autre plug-in (par exemple, [!INCLUDE[vsvss](../../includes/vsvss-md.md)]).<br />6.  Recharger la solution à partir du disque si déchargé.<br />7.  Ajouter la solution au contrôle de code source.<br />8.  Déconnectez la solution de contrôle de code source (à l’aide de **modifier le contrôle de Source** boîte de dialogue).<br />9. Sélectionnez le plug-in de test à nouveau.<br />10. Rechargez la solution à partir du disque si déchargé.<br />11. Lier la solution à l’emplacement d’origine (à l’aide de la **modifier le contrôle de Source** boîte de dialogue).|Solution est ajoutée au contrôle de code source à l’aide du plug-in.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

