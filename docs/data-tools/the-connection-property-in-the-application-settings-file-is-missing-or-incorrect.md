---
title: La propriété de connexion est manquante ou incorrecte dans le fichier des paramètres de l'application
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: db0ac06d26e7e597d9f8d4b3c11a9cf8db188e80
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174125"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>La propriété de connexion est manquante ou incorrecte dans le fichier des paramètres de l'application

La propriété de connexion dans le fichier des paramètres de l'application est manquante ou incorrecte. La chaîne de connexion à partir de la *.dbml* fichier a été utilisé à la place.

Le *.dbml* fichier contient une référence à une chaîne de connexion dans le fichier de paramètres d’application qui est introuvable. Ce message est informatif ; le paramètre de chaîne de connexion sera créé dès **OK** est cliqué.

Pour répondre à ce message, sélectionnez **OK**. Les informations de connexion qui sont contenues dans le *.dbml* fichier est ajouté aux paramètres d’application.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)