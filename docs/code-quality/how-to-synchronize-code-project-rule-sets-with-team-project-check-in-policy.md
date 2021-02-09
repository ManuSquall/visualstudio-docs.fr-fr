---
title: Synchroniser les ensembles de règles de projet avec la stratégie d’archivage
ms.date: 11/04/2016
description: Découvrez comment synchroniser un ensemble de règles de projet Visual Studio code avec une stratégie d’archivage de projet Azure DevOps.
ms.custom: SEO-VS-2020
ms.topic: how-to
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2908f7ec93d8704b52798121bd0076a7f5fddc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859916"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Procédure : synchroniser des ensembles de règles de projet de code avec une stratégie d’archivage de projet Azure DevOps

Vous synchronisez les paramètres d’analyse du code des projets de code avec la stratégie d’archivage du projet Azure DevOps en spécifiant un ensemble de règles qui contient au moins les règles spécifiées dans l’ensemble de règles pour la stratégie d’archivage. Votre responsable de développeur peut vous informer du nom et de l’emplacement de l’ensemble de règles pour la stratégie d’archivage. Vous pouvez utiliser l’une des options suivantes pour vous assurer que l’analyse du code du projet utilise l’ensemble de règles correct :

- Si la stratégie d’archivage utilise l’un des ensembles de règles intégrés Microsoft, ouvrez la boîte de dialogue Propriétés du projet de code, affichez la page analyse du code, puis sélectionnez l’ensemble de règles. Les ensembles de règles standard Microsoft sont installés automatiquement avec Visual Studio qui sont définis en lecture seule et ne doivent pas être modifiés. Si les ensembles de règles ne sont pas modifiés, il est garanti que les règles de la stratégie et les ensembles de règles locaux correspondent.

- Si la stratégie d’archivage utilise un ensemble de règles personnalisé, effectuez une opération d’extraction sur le fichier d’ensemble de règles dans le contrôle de version pour créer une copie locale. Spécifiez ensuite cet emplacement local dans les paramètres d’analyse du code pour le projet de code. La correspondance des règles est garantie si l’ensemble de règles de la stratégie d’archivage est à jour.

     Si vous mappez l’emplacement de contrôle de version à un dossier local qui se trouve dans la même relation à la racine du projet Azure DevOps que votre projet de code, l’emplacement de la règle est défini à l’aide d’un chemin d’accès relatif. Le chemin d’accès relatif garantit que le paramètre du projet de code pour l’analyse du code peut être déplacé vers d’autres ordinateurs.

- Personnaliser une copie de l’ensemble de règles pour la stratégie d’archivage pour un projet de code. Assurez-vous que le nouvel ensemble de règles contient toutes les règles de la stratégie d’archivage et toutes les autres règles que vous souhaitez inclure. Vous devez vous assurer que votre ensemble de règles contient toutes les règles de l’ensemble de règles pour la stratégie d’archivage.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Pour spécifier un ensemble de règles standard Microsoft

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.

2. Cliquez sur **Analyse du code**.

::: moniker range="vs-2017"

3. Dans la liste **exécuter cet ensemble de règles** , sélectionnez l’ensemble de règles de stratégie d’archivage.

::: moniker-end

::: moniker range=">=vs-2019"

3. Dans la liste **règles actives** , sélectionnez l’ensemble de règles de stratégie d’archivage.

::: moniker-end

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Pour spécifier un ensemble de règles de stratégie d’archivage personnalisé

1. Si nécessaire, effectuez une opération d’extraction sur le fichier d’ensemble de règles qui spécifie la stratégie d’archivage.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.

3. Cliquez sur **Analyse du code**.

::: moniker range="vs-2017"

4. Dans la liste **exécuter cet ensemble de règles** , cliquez sur **\<Browse>** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Dans la liste **règles actives** , cliquez sur **\<Browse>** .

::: moniker-end

5. Dans la boîte de dialogue **ouvrir** , spécifiez le fichier d’ensemble de règles de stratégie d’archivage.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Pour créer un ensemble de règles personnalisé pour un projet de code

Pour plus d’informations sur la création d’un ensemble de règles personnalisé, consultez [personnaliser un ensemble de règles](how-to-create-a-custom-rule-set.md).
