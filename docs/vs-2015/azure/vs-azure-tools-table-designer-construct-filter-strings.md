---
title: Construction de chaînes de filtre pour le Concepteur de tables | Microsoft Docs
description: Construction de chaînes de filtre pour le Concepteur de tables
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001965"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Construction de chaînes de filtre pour le Concepteur de tables
## <a name="overview"></a>Vue d'ensemble
Pour filtrer les données dans une table Azure qui s’affiche dans Visual Studio **Concepteur de tables**, vous construisez une chaîne de filtrage et entrez-le dans le champ de filtre. La syntaxe de chaîne de filtre est définie par les Services de données WCF et est similaire à une clause SQL WHERE, mais est envoyée au service de Table via une requête HTTP. Le **Concepteur de tables** gère l’encodage pour vous, donc pour filtrer sur une valeur de propriété souhaitée, vous devez uniquement entrer le nom de propriété, opérateur de comparaison, valeur des critères et si vous le souhaitez, valeur booléenne opérateur dans le champ filtre. Vous n’avez pas besoin d’inclure l’option de requête $filter comme vous le feriez si vous construisiez une URL pour interroger la table via le [référence de l’API REST Storage Services](http://go.microsoft.com/fwlink/p/?LinkId=400447).

Les Services de données WCF sont basés sur le [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Pour plus d’informations sur l’option de requête système filter (**$filter**), consultez le [spécifications OData URI Conventions](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Opérateurs de comparaison
Les opérateurs logiques suivants sont pris en charge pour tous les types de propriété :

| Opérateur logique | Description | Exemple de chaîne de filtre |
| --- | --- | --- |
| eq |Égal |Ville eq 'Redmond' |
| gt |Supérieur à |Prix gt 20 |
| GE |Supérieur ou égal à |Prix ge 10 |
| lt |Inférieur à |Prix lt 20 |
| le |Inférieur ou égal à |Prix le 100 |
| Nou |Différence |Ville ne 'Londres' |
| et |Et |Prix le 200 and prix gt 3,5 |
| ou |Ou |Prix le 3,5 or prix gt 200 |
| not |Ne convient pas |pas d’isAvailable |

Lors de la construction d’une chaîne de filtrage, les règles suivantes sont importantes :

* Utilisez les opérateurs logiques pour comparer une propriété à une valeur. Notez qu’il n’est pas possible de comparer une propriété à une valeur dynamique ; côté « un » de l’expression doit être une constante.
* Toutes les parties de la chaîne de filtrage respectent la casse.
* La valeur de constante doit être du même type de données en tant que la propriété afin que le filtre pour retourner des résultats valides. Pour plus d’informations sur les types de propriété pris en charge, consultez [présentation du modèle de données de Service de Table](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Filtrage sur les propriétés de chaîne
Lorsque vous filtrez sur les propriétés de chaîne, placez la constante de chaîne entre guillemets simples.

L’exemple suivant filtre sur le **PartitionKey** et **RowKey** propriétés ; non clé supplémentaire propriétés peuvent également être ajoutées à la chaîne de filtrage :

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Vous pouvez placer chaque expression de filtre entre parenthèses, même s’il n’est pas nécessaire :

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Notez que le service de Table ne prend pas en charge les requêtes à caractères génériques, et ils ne sont pas pris en charge dans le Concepteur de tables soit. Toutefois, vous pouvez effectuer la correspondance sur le préfixe souhaité à l’aide des opérateurs de comparaison de préfixe. L’exemple suivant retourne des entités avec une propriété LastName commençant par la lettre « A » :

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Filtrage par propriété numérique
Pour filtrer sur un entier ou un nombre à virgule flottante, spécifiez le nombre sans guillemets.

Cet exemple retourne toutes les entités avec une propriété Age dont la valeur est supérieure à 30 :

    Age gt 30

Cet exemple retourne toutes les entités avec une propriété AmountDue a dont la valeur est inférieure ou égale à 100,25 :

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Filtrage par propriété booléenne
Pour filtrer sur une valeur booléenne, spécifiez **true** ou **false** sans guillemets.

L’exemple suivant retourne toutes les entités où la propriété IsActive a la valeur **true**:

    IsActive eq true

Vous pouvez également écrire cette expression de filtre sans opérateur logique. Dans l’exemple suivant, le service de Table retournera également toutes les entités où IsActive est **true**:

    IsActive

Pour retourner toutes les entités où IsActive a la valeur false, vous pouvez utiliser not opérateur :

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Filtrage sur les propriétés de date/heure
Pour filtrer sur une valeur DateTime, spécifiez la **datetime** mot clé, suivi par la constante de date/heure entre guillemets simples. La constante de date/heure doit être au format UTC combiné, comme décrit dans [mise en forme des valeurs de propriété DateTime](http://go.microsoft.com/fwlink/p/?LinkId=400449).

L’exemple suivant retourne les entités où la propriété CustomerSince est égale à 10 juillet 2008 :

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
