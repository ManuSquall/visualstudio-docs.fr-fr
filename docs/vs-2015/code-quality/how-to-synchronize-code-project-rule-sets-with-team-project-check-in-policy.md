---
title: 'Comment : synchroniser des ensembles de règles de projet de code avec la stratégie d’archivage du projet d’équipe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651601"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Comment : synchroniser des ensembles de règles applicables à des projets de code avec la stratégie d'archivage du projet d'équipe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous synchronisez les paramètres d’analyse du code des projets de code avec la stratégie d’archivage du projet d’équipe en spécifiant un ensemble de règles qui contient au moins les règles spécifiées dans l’ensemble de règles pour la stratégie d’archivage. Votre responsable de développeur peut vous informer du nom et de l’emplacement de l’ensemble de règles pour la stratégie d’archivage. Vous pouvez utiliser l’une des options suivantes pour vous assurer que l’analyse du code du projet utilise l’ensemble de règles correct :

- Si la stratégie d’archivage utilise l’un des ensembles de règles intégrés Microsoft, ouvrez la boîte de dialogue Propriétés du projet de code, affichez la page analyse du code, puis sélectionnez l’ensemble de règles dans la page analyse du code des paramètres du projet de code. Les ensembles de règles standard Microsoft sont installés automatiquement avec Visual Studio qui sont définis en lecture seule et ne doivent pas être modifiés. Si les ensembles de règles ne sont pas modifiés, il est garanti que les règles de la stratégie et les ensembles de règles locaux correspondent.

- Si la stratégie d’archivage utilise un ensemble de règles personnalisé, effectuez une opération d’extraction sur le fichier d’ensemble de règles dans le contrôle de version pour créer une copie locale. Spécifiez ensuite cet emplacement local dans les paramètres d’analyse du code pour le projet de code. La correspondance des règles est garantie si l’ensemble de règles de la stratégie d’archivage est à jour.

     Si vous mappez l’emplacement de contrôle de version à un dossier local qui se trouve dans la même relation à la racine du projet d’équipe que votre projet de code, l’emplacement de la règle est défini à l’aide d’un chemin d’accès relatif. Le chemin d’accès relatif garantit que le paramètre du projet de code pour l’analyse du code peut être déplacé vers d’autres ordinateurs.

- Personnaliser une copie de l’ensemble de règles pour la stratégie d’archivage pour un projet de code. Assurez-vous que le nouvel ensemble de règles contient toutes les règles de la stratégie d’archivage et toutes les autres règles que vous souhaitez inclure. Vous devez vous assurer que votre ensemble de règles contient toutes les règles de l’ensemble de règles pour la stratégie d’archivage.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>Pour spécifier un ensemble de règles standard Microsoft

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.

2. Cliquez sur **Analyse du code**.

3. Dans la liste **exécuter cet ensemble de règles** , cliquez sur l’ensemble de règles de stratégie d’archivage.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Pour spécifier un ensemble de règles de stratégie d’archivage personnalisé

1. Si nécessaire, effectuez une opération d’extraction sur le fichier d’ensemble de règles qui spécifie la stratégie d’archivage.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.

3. Cliquez sur **Analyse du code**.

4. Dans la liste **exécuter cet ensemble de règles** , cliquez sur **\<Browse...>** .

5. Dans la boîte de dialogue **ouvrir** , spécifiez le fichier d’ensemble de règles de stratégie d’archivage.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Pour créer un ensemble de règles personnalisé pour un projet de code

1. Suivez l’une des procédures décrites précédemment dans cette rubrique pour sélectionner la stratégie d’archivage du projet d’équipe dans la page analyse du code de la boîte de dialogue Paramètres du projet.

2. Cliquez sur **Ouvrir**.

3. Ajoutez ou supprimez des règles à l’aide de l’éditeur d’ensembles de règles.

     Pour plus d’informations, consultez [création d’ensembles de règles personnalisées](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Enregistrez l’ensemble de règles modifié dans un fichier. RuleSet sur l’ordinateur local ou dans un chemin d’accès UNC.

5. Ouvrez la boîte de dialogue Propriétés du projet de code, puis affichez la page **analyse du code** .

6. Dans la liste **exécuter cet ensemble de règles** , cliquez sur **\<Browse...>** .

7. Dans la boîte de dialogue **ouvrir** , spécifiez le fichier d’ensemble de règles.
