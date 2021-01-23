---
title: Définir les options de nom de fichier de données de profilage | Microsoft Docs
description: Découvrez comment vous pouvez modifier n’importe quel paramètre de nommage sur la page général de la boîte de dialogue Propriétés de la session de performance.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6dce666121214bef7d844bae2735a284589463ee
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722046"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Guide pratique pour définir les options de nom de fichier des données de performance

Par défaut, vous enregistrez un fichier de données de profilage (.*vsp*) à l’aide de la syntaxe suivante :

*Chemin\Fichier_VSP\AAMMJJ(N)* **.vsp**

Vous pouvez modifier tout paramètre d’attribution de nom dans la page **Général** de la boîte de dialogue des propriétés pour la session de performance.

|Paramètre|Description|
|-|-|
|*Chemin d’accès*|Répertoire qui contient le rapport. L’emplacement par défaut est le dossier de solution ou l’emplacement par défaut pour les projets et solutions de l’utilisateur.|
|*VSP-fichier*|Nom du fichier de données de profilage. Le nom par défaut est le nom de la solution ou du fichier exécutable profilés.|
|*AAMMJJ*|Horodatage qui affiche l’année, le mois et le jour auxquels les données de profilage ont été collectées.|
|*N*|S’il existe plusieurs fichiers de données de profilage, un nombre incrémenté est ajouté entre parenthèses au nom du fichier.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Pour modifier la syntaxe d’attribution de noms des fichiers de données de profilage d’une session de performance

1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur le nom de la session de performance, puis cliquez sur **Propriétés**.

2. Cliquez sur **Général**.

3. Sous **Rapport**, modifiez les paramètres suivants :

    |Name|Description|
    |-|-|
    |**Emplacement du rapport**|Spécifiez un répertoire pour le stockage des fichiers de données de profilage.|
    |**Nom du rapport**|Spécifiez un nom de base pour les fichiers.|
    |**Ajouter automatiquement de nouveaux rapports à la session**|Cochez la case pour ajouter automatiquement le fichier de données à la session de performance.|
    |**Ajouter un numéro à incrémentation aux rapports générés**|Cochez la case pour ajouter un numéro à incrémentation au nom du fichier quand il existe plusieurs fichiers du même nom. Décochez la case pour remplacer un fichier existant.|
    |**Utiliser un horodatage pour le nombre**|Cochez la case pour ajouter un horodatage au nom du fichier.|
