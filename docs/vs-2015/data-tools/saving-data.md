---
title: L’enregistrement des données | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: dc671d60ff37e9853dc64a62cbc1b91a6914e0e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249299"
---
# <a name="saving-data"></a>Enregistrement de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’enregistrement des données est que le processus de persistance a modifié des données dans le modèle de données d’une application dans le magasin de données d’origine, généralement une base de données relationnel telles que SQL Server.  
  
 La mise à jour d’une source de données au moyen d’un modèle de données est généralement un processus en deux étapes. La première étape consiste à mettre à jour le modèle de données avec de nouvelles informations : nouveaux enregistrements, enregistrements modifiés ou supprimés des enregistrements. La deuxième étape consiste à enregistrer les modifications dans votre modèle de données à la base de données.  
  
 Les rubriques suivantes décrivent les concepts et les tâches associées à l’enregistrement des données.  
  
## <a name="related-topics"></a>Rubriques connexes  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)  
 Fournit une vue d’ensemble de la façon dont les modifications sont apportées dans un jeu de données et comment le jeu de données effectue le suivi des informations sur les modifications pour enregistrer ces modifications dans une base de données.  
  
 [Enregistrement des Entity Data](../data-tools/saving-entity-data.md)  
 Décrit comment enregistrer les modifications dans [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) et [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) applications.