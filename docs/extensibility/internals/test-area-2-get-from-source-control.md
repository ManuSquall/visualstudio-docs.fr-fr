---
title: 'Zone d’essai 2 : Obtenez du contrôle des sources Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704601"
---
# <a name="test-area-2-get-from-source-control"></a>Zone de test 2 : Obtenir à partir du contrôle de code source
Cette zone de test couvre les cas de test pour la récupération d’articles à partir du magasin de version via la commande Get. Ces cas de test peuvent être appliqués à la fois aux projets locaux et aux projets Web.

## <a name="command-menu-access"></a>Accès au menu de commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours de menu intégrés suivants sont utilisés dans les cas d’essai.

##### <a name="get-latest-version"></a>Obtenez la dernière version:

- **Fichier**, **Contrôle source**, Obtenez la **dernière version**.

- **Fichier**, **Obtenez la dernière version**.

- Menu raccourci, **Get Latest Version**.

- Obtenir: **Fichier**, **Contrôle source**, **Obtenez**.

## <a name="expected-behavior"></a>Comportement attendu

##### <a name="get-latest-version"></a>Obtenez la dernière version:
 Effectue une récupération silencieuse (sans interface utilisateur) de la dernière version de l’article à partir du magasin de version.

##### <a name="get"></a>Obtenir :
 Affiche la boîte de dialogue **Get** et permet à l’utilisateur d’apporter des modifications à l’ensemble de fichiers qui seront récupérés ainsi que de modifier les options qui affectent la façon dont les fichiers sont récupérés.

## <a name="test-cases"></a>Cas de test

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Obtenez la dernière version d’un fichier qui n’existe pas localement|1. Créer un projet.<br />2. Ajouter un élément au projet.<br />3. Mettre le projet sous contrôle source.<br />4. Supprimer la copie locale de l’élément.<br />5. Obtenez la dernière version de l’article (Menu raccourci, **Obtenez la dernière version**).|Le fichier d’objets est récupéré localement.|
|Obtenez un fichier qui n’existe PAS localement|1. Créer un projet.<br />2. Ajouter un élément au projet.<br />3. Mettre le projet sous contrôle source.<br />4. Supprimer la copie locale de l’élément.<br />5. Obtenez l’article **(Fichier**, **Contrôle source**, **Obtenez** \<l’élément>).|Le fichier d’objets est récupéré localement.|
|Obtenez un fichier qui a été vérifié exclusivement et modifié localement|1. Créer un projet.<br />2. Ajouter un élément au projet.<br />3. Mettre le projet sous contrôle source.<br />4. Consultez l’élément du projet exclusivement.<br />5. Modifier la copie locale.<br />6. Obtenez la dernière version de l’élément **(Fichier**, **Obtenez la dernière version de l’article** \<>). Si cette étape réussit, continuez à passer à l’étape suivante.<br />7. Cliquez sur le bouton **Remplacer** dans la boîte de dialogue d’avertissement.|**ReResult de l’étape 6**`:`<br /><br /> La boîte de dialogue d’avertissement indique que le fichier est coché.<br /><br /> **ReResult de l’étape 7:**<br /><br /> Le fichier local modifié est remplacé par la version originale du magasin de version.<br /><br /> Le fichier est lu/écriture.|
|Obtenez et remplacez le fichier qui est vérifié, partagé et modifié localement|1. Créer un nouveau projet.<br />2. Ajouter un élément au projet.<br />3. Mettre le projet sous contrôle source.<br />4. Consultez l’élément du projet tel que partagé.<br />5. Modifier la copie locale.<br />6. Obtenez la dernière version de l’élément **(Fichier**, **Obtenez la dernière version de l’article** \<>). Si cette étape réussit, continuez à passer à l’étape suivante.<br />7. Cliquez sur **Remplacer** dans la boîte de dialogue d’avertissement.|**Résultat de l’étape 6:**<br /><br /> La boîte de dialogue d’avertissement indique que le fichier est coché.<br /><br /> **Résultat de l’étape 7:**<br /><br /> Le fichier local modifié est remplacé par la version originale du magasin de version.<br /><br /> Le fichier est lu/écriture.|
|Obtenez un fichier qui existe localement, comme la dernière version dans le magasin de version|1. Créer un nouveau projet.<br />2. Ajouter un élément au projet.<br />3. Mettre le projet sous contrôle source.<br />4. Obtenez l’article **(Fichier**, **Contrôle source**, **Obtenez** \<l’élément>).|Le fichier local est inchangé.|
|Obtenir une solution avec un seul projet|1. Créer une solution avec un seul projet.<br />2. Placer la solution sous contrôle source.<br />3. Supprimer tous les fichiers de projet localement.<br />4. Obtenez la solution (**Fichier**, **Contrôle source**, **Get**).|Tous les fichiers supprimés sont restaurés localement.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
