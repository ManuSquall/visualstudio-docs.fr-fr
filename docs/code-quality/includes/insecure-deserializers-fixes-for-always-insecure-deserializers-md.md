---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147110"
---
- Si possible, utilisez à la place, un sérialiseur sécurisé et **ne pas autoriser une personne malveillante spécifier un type arbitraire à désérialiser**. Certains sérialiseurs plus sûres sont les suivantes :
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> : Ne jamais utiliser <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Si vous devez utiliser un résolveur de type, restreindre les types désérialisées à une liste attendue.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - utiliser TypeNameHandling.None. Si vous devez utiliser une autre valeur pour TypeNameHandling, restreindre les types désérialisées à une liste attendue avec un ISerializationBinder personnalisé.
  - Mémoires tampons de protocole
- Vérifiez la falsification de données sérialisées. Après la sérialisation, signer par chiffrement les données sérialisées. Avant la désérialisation, valider la signature de chiffrement. Protéger la clé de chiffrement ne soient divulgués et de la conception pour les rotations de clés.