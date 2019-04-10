---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367267"
---
Désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non fiables. Un attaquant pourrait modifier les données sérialisées pour inclure les types inattendus avec effets secondaires malveillants. Une attaque contre un désérialiseur non sécurisé peut, par exemple, exécuter des commandes sur le système d’exploitation sous-jacent, communiquer sur le réseau ou supprimer des fichiers.