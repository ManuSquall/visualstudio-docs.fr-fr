---
title: Construction de chaînes de filtrage pour le Concepteur de tables | Microsoft Docs
description: Construction de chaînes de filtrage pour le Concepteur de tables
author: ghogen
manager: jillfra
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: d19084e9cfc9813434f5e68829345440763df7e8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929282"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Construction de chaînes de filtrage pour le Concepteur de tables
## <a name="overview"></a>Vue d'ensemble
Pour filtrer les données d’une table Azure affichée dans le **Concepteur de tables** Visual Studio, vous devez créer une chaîne de filtrage, puis entrer celle-ci dans le champ de filtre. La syntaxe de la chaîne de filtrage est définie par les services de données WCF et est similaire à une clause SQL WHERE. Cependant, elle est envoyée au service de Table via une demande HTTP. Le **Concepteur de tables** est chargé de l’encodage. Si vous voulez filtrer les données à l’aide d’une valeur de propriété, il vous suffit donc de taper dans le champ de filtrage le nom de la propriété, l’opérateur de comparaison, la valeur des critères et éventuellement, l’opérateur booléen. Il n’est pas nécessaire d’inclure l’option de requête $filter comme vous le feriez pour créer une URL dans le but d’interroger la table via les [informations de référence de l’API REST Storage Services](http://go.microsoft.com/fwlink/p/?LinkId=400447).

Les services de données WCF sont basés sur le protocole OData ( [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) ). Pour plus d’informations sur l’option de requête du système de filtrage (**$filter**), consultez les [spécifications des conventions d’URI OData](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Opérateurs de comparaison
Les opérateurs logiques suivants sont pris en charge par tous les types de propriétés :

| Opérateur logique | Description | Exemple de chaîne de filtrage |
| --- | --- | --- |
| eq |Égal à |Ville eq 'Redmond' |
| gt |Supérieur à |Prix gt 20 |
| ge |Supérieur ou égal à |Prix ge 10 |
| lt |Inférieur à |Prix lt 20 |
| le |Inférieur ou égal à |Prix le 100 |
| ne |Non égal à |Ville ne 'Londres' |
| et |and |Prix le 200 and prix gt 3,5 |
| ou |Ou |Prix le 3,5 or prix gt 200 |
| not |not |not isAvailable |

Quand vous créez une chaîne de filtrage, il est important de suivre les règles suivantes :

* Utilisez les opérateurs logiques pour comparer une propriété à une valeur. Notez qu’il n’est pas possible de comparer une propriété à une valeur dynamique, car l’une des parties de l’expression doit avoir une valeur constante.
* Toutes les parties de la chaîne de filtrage respectent la casse.
* Pour que le filtre retourne des résultats valides, la valeur constante doit être du même type de données que la propriété. Pour plus d’informations sur les types de propriétés pris en charge, consultez [Présentation du modèle de données du service de Table](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Filtrage par propriété de chaîne
Quand vous filtrez des données selon des propriétés de chaîne, placez la constante de chaîne entre guillemets simples.

L’exemple suivant filtre les données selon les propriétés **PartitionKey** et **RowKey**. D’autres propriétés non-clés peuvent également être ajoutées à la chaîne de filtrage :

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Vous pouvez placer chaque expression de filtrage entre parenthèses, même si cela n’est pas obligatoire :

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Notez que le service de Table et le Concepteur de tables ne prennent pas en charge les requêtes génériques. Toutefois, vous pouvez lancer une correspondance de préfixe à l’aide d’opérateurs de comparaison sur le préfixe de votre choix. L’exemple suivant retourne des entités avec une propriété LastName commençant par la lettre « A » :

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Filtrage par propriété numérique
Pour filtrer les données selon un nombre entier ou un nombre à virgule flottante, spécifiez le nombre sans utiliser de guillemets.

Cet exemple retourne toutes les entités dont la propriété Age a une valeur supérieure à 30 :

    Age gt 30

Cet exemple retourne toutes les entités dont la propriété AmountDue a une valeur inférieure ou égale à 100,25 :

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Filtrage par propriété booléenne
Pour filtrer les données à l’aide d’une valeur booléenne, spécifiez **true** ou **false** sans guillemets.

L’exemple suivant retourne toutes les entités dont la propriété IsActive a la valeur **true**:

    IsActive eq true

Vous pouvez également écrire cette expression de filtre sans opérateur logique. Dans l’exemple suivant, le service de Table retournera également toutes les entités dont la propriété IsActive a la valeur **true**:

    IsActive

Pour retourner toutes les entités dont la propriété IsActive a la valeur false, vous pouvez utiliser l’opérateur not :

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Filtrage par propriété DateTime
Pour filtrer les données à l’aide d’une valeur DateTime, spécifiez le mot clé **datetime** , suivi de la constante Date/Heure entre guillemets simples. La constante Date/Heure doit être au format UTC combiné, comme décrit dans [Mise en forme des valeurs de propriété DateTime](http://go.microsoft.com/fwlink/p/?LinkId=400449).

L’exemple suivant retourne les entités dont la propriété CustomerSince a la valeur « 10 juillet 2008 » :

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
