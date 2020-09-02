---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471573"
---
- Utilisez un sérialiseur sécurisé à la place et **n’autorisez pas une personne malveillante à spécifier un type arbitraire à désérialiser**. Pour plus d’informations, consultez les [alternatives recommandées](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Rendez la falsification des données sérialisées. Après la sérialisation, signez les données sérialisées par chiffrement. Avant la désérialisation, validez la signature de chiffrement. Empêcher la clé de chiffrement d’être divulguée et concevoir des rotations de clés.
- Grâce à cette option, le code est vulnérable aux attaques par déni de service et à l’exécution de code à distance possible à l’avenir. Pour plus d’informations, consultez le [Guide de sécurité BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide). Limitez les types désérialisés. Implémentez un personnalisé <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Avant la désérialisation, affectez `Binder` à la propriété une instance de votre personnalisé <xref:System.Runtime.Serialization.SerializationBinder> dans tous les chemins de code. Dans la méthode substituée <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , si le type est inattendu, levez une exception pour arrêter la désérialisation.
