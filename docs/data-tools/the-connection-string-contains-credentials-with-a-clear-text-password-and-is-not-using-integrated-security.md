---
title: La chaîne de connexion contient des informations d'identification comprenant un mot de passe en texte clair et n'utilise pas la sécurité intégrée
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ef63abe36a5880305f522d75d9e1cb1d7f6995fa
ms.sourcegitcommit: 59c48e1e42b48ad25a4e198af670faa4d8dae370
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204201"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La chaîne de connexion contient des informations d'identification comprenant un mot de passe en texte clair et n'utilise pas la sécurité intégrée

Voulez-vous enregistrer la chaîne de connexion dans le fichier DBML actuel et les fichiers de configuration de l'application avec ces informations confidentielles ?  Cliquez sur **Non** pour enregistrer la chaîne de connexion sans les informations confidentielles.

Lorsque vous travaillez avec des connexions de données qui incluent des informations confidentielles (mots de passe inclus dans la chaîne de connexion), vous pouvez enregistrer la chaîne de connexion dans le fichier DBML et le fichier de configuration de l'application du projet, avec ou sans les informations confidentielles.

> [!WARNING]
> Si vous affectez explicitement à la propriété **Paramètres de l’application** des propriétés de **connexion** la valeur **False**, le mot de passe sera ajouté au fichier DBML.

## <a name="save-options"></a>Options d’enregistrement

- Pour enregistrer la chaîne de connexion avec les informations sensibles, choisissez **Oui**.

   La chaîne de connexion est stockée en tant que paramètre d'application. La chaîne de connexion intègre les informations sensibles dans le texte brut. Le fichier DBML ne contient pas les informations sensibles.

- Pour enregistrer la chaîne de connexion sans les informations confidentielles, choisissez **non**.

   La chaîne de connexion est stockée en tant que paramètre d'application, mais le mot de passe n'est pas inclus.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)