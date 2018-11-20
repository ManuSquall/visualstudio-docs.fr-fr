---
title: 'Zone de test 2 : Obtenir à partir du contrôle de code Source | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b00cfc9965b6006fa51b3cd313566658d604bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786156"
---
# <a name="test-area-2-get-from-source-control"></a>Zone de test 2 : Obtenir à partir du contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette zone de test traite des cas de test pour la récupération des éléments à partir de la banque des versions par le biais de la commande Get. Ces cas de test peuvent être appliquées aux deux types et aux projets Web.  
  
## <a name="command-menu-access"></a>Accès au Menu de commande  
 Ce qui suit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test.  
  
##### <a name="get-latest-version"></a>Obtenir la dernière Version :  
  
-   **Fichier**, **contrôle de code Source**, **obtenir la dernière Version**.  
  
-   **Fichier**, **obtenir la dernière Version**.  
  
-   Menu contextuel, **obtenir la dernière Version**.  
  
-   Get : **fichier**, **contrôle de code Source**, **obtenir**.  
  
## <a name="expected-behavior"></a>Comportement attendu  
  
##### <a name="get-latest-version"></a>Obtenir la dernière Version :  
 Effectue une extraction en mode silencieux (aucune interface utilisateur) de la dernière version de l’élément à partir de la banque des versions.  
  
##### <a name="get"></a>Télécharger :  
 Affiche le **obtenir** boîte de dialogue et permet à l’utilisateur apporter des modifications à l’ensemble de fichiers qui est récupéré, ainsi que pour modifier les options qui affectent la façon dont les fichiers sont récupérés.  
  
## <a name="test-cases"></a>Cas de test  
  
|Action|Étapes de test|Résultats attendus pour vérifier|  
|------------|----------------|--------------------------------|  
|Obtenir la dernière Version d’un fichier qui n’existe pas localement|1.  Créez un projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Supprimer la copie locale de l’élément.<br />5.  Obtenir la dernière Version de l’élément (Menu contextuel, **obtenir la dernière Version**).|Fichier de l’élément est récupéré localement.|  
|Obtenir un fichier qui n’existe pas localement|1.  Créez un projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Supprimer la copie locale de l’élément.<br />5.  Obtenir l’élément (**fichier**, **contrôle de code Source**, **obtenir** \<élément >).|Fichier de l’élément est récupéré localement.|  
|Obtenir un fichier qui a été extrait en mode exclusif et modifié localement|1.  Créez un projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Consultez l’élément de projet exclusivement.<br />5.  Modifier la copie locale.<br />6.  Obtenir la dernière Version de l’élément (**fichier**, **obtenir la dernière Version de** \<élément >). Si cette étape réussit, passez à l’étape suivante.<br />7.  Cliquez sur **remplacer** bouton dans la boîte de dialogue d’avertissement.|**ReResult à l’étape 6** `:`<br /><br /> Boîte de dialogue d’avertissement indique que ce fichier est extrait.<br /><br /> **ReResult à l’étape 7 :**<br /><br /> Fichier local modifié est remplacée par la version d’origine à partir de la banque des versions.<br /><br /> Fichier est en lecture/écriture.|  
|Obtenez et remplacez le fichier qui est extrait, partagé et modifié localement|1.  Créer un nouveau projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Consultez l’élément de projet comme partagée.<br />5.  Modifier la copie locale.<br />6.  Obtenir la dernière Version de l’élément (**fichier**, **obtenir la dernière Version de** \<élément >). Si cette étape réussit, passez à l’étape suivante.<br />7.  Cliquez sur **remplacer** dans la boîte de dialogue d’avertissement.|**Résultat de l’étape 6 :**<br /><br /> Boîte de dialogue d’avertissement indique que ce fichier est extrait.<br /><br /> **Résultat de l’étape 7 :**<br /><br /> Fichier local modifié est remplacée par la version d’origine à partir de la banque des versions.<br /><br /> Fichier est en lecture/écriture.|  
|Obtenir un fichier qui n’existe pas localement, même en tant que la version la plus récente dans la banque des versions|1.  Créer un nouveau projet.<br />2.  Ajouter un élément au projet.<br />3.  Placer le projet sous contrôle de code source.<br />4.  Obtenir l’élément (**fichier**, **contrôle de code Source**, **obtenir** \<élément >).|Fichier local est inchangé.|  
|Bénéficiez d’une solution avec un projet|1.  Créer une solution avec un projet.<br />2.  Placez la solution sous contrôle de code source.<br />3.  Supprimer tous les fichiers projet localement.<br />4.  Obtenir la solution (**fichier**, **contrôle de code Source**, **obtenir**).|Tous les fichiers supprimés sont restaurés localement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

