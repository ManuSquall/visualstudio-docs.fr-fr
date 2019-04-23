---
title: Définition d'une stratégie de verrouillage pour créer des segments en lecture seule
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38f81b3269d0a456c077023d23861a55ac06a4c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117187"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Définition d'une stratégie de verrouillage pour créer des segments en lecture seule
L’API d’immuabilité de la Visual Studio Visualization and Modeling SDK permet à un programme verrouiller tout ou partie d’un modèle de langage spécifique à un domaine (DSL) afin qu’il peut être lue mais pas modifié. Cette option en lecture seule peut être utilisée, par exemple, afin qu’un utilisateur peut demander à vos collègues à annoter et passez en revue un modèle DSL, mais leur interdire de modifier l’original.

 En outre, en tant qu’auteur d’un DSL, vous pouvez définir un *stratégie de verrouillage.* Une stratégie de verrouillage définit quels verrous sont autorisés, non autorisé ou obligatoire. Par exemple, lorsque vous publiez une solution DSL, vous pouvez encourager les développeurs tiers pour l’étendre avec de nouvelles commandes. Mais vous pouvez également utiliser une stratégie de verrouillage pour les empêcher de modifier l’état en lecture seule des parties spécifiées du modèle.

> [!NOTE]
>  Une stratégie de verrouillage peut être contournée en utilisant la réflexion. Il fournit une limite pour les développeurs tiers, mais ne fournit pas une sécurité renforcée.

 Plus d’informations et exemples sont disponibles dans Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) site Web.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Définition et obtention de verrous
 Vous pouvez définir des verrous sur le magasin, sur une partition ou sur un élément individuel. Par exemple, cette instruction empêche un élément de modèle de suppression et également empêchera ses propriétés en cours de modification :

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Autres valeurs de verrouillage peuvent être utilisées pour empêcher les modifications dans les relations, la création d’élément, le déplacement entre des partitions et des liens de nouveau classement dans un rôle.

 Les verrous s’appliquent aux actions de l’utilisateur et au code de programme. Si le code de programme tente d’apporter une modification, une `InvalidOperationException` sera levée. Les verrous sont ignorés dans une opération d’annulation ou de rétablissement.

 Vous pouvez découvrir si un élément a un verrou quelconque dans un ensemble donné à l’aide de `IsLocked(Locks)` et vous pouvez obtenir l’ensemble actuel de verrous sur un élément à l’aide de `GetLocks()`.

 Vous pouvez définir un verrou sans utiliser une transaction. La base de données de verrou ne fait pas partie du magasin. Si vous définissez un verrou en réponse à une modification d’une valeur dans le magasin, par exemple dans OnValueChanged, vous devez autoriser les modifications qui font partie d’une opération d’annulation.

 Ces méthodes sont des méthodes d’extension qui sont définies dans le <xref:Microsoft.VisualStudio.Modeling.Immutability> espace de noms.

### <a name="locks-on-partitions-and-stores"></a>Verrous sur les partitions et de magasins
 Verrous peuvent également être appliqués aux partitions et le magasin. Un verrou qui est défini sur une partition s’applique à tous les éléments dans la partition. Par conséquent, par exemple, l’instruction suivante empêche tous les éléments dans une partition d’être supprimé, quel que soit les États de leurs propres verrous. Néanmoins, d’autres verrous comme `Locks.Property` peut toujours être définies sur des éléments individuels :

```csharp
partition.SetLocks(Locks.Delete);
```

 Un verrou qui est défini sur le Store s’applique à tous ses éléments, quel que soit les paramètres de ce verrou sur les partitions et les éléments.

### <a name="using-locks"></a>L’utilisation de verrous
 Vous pouvez utiliser des verrous pour implémenter des schémas tels que les exemples suivants :

- Interdire les modifications apportées à tous les éléments et les relations à l’exception de ceux qui représentent des commentaires. Cela permet aux utilisateurs d’annoter un modèle sans le modifier.

- Interdire les modifications dans la partition par défaut, mais autoriser les modifications dans la partition de schéma. L’utilisateur peut réorganiser le diagramme, mais vous ne pouvez pas modifier le modèle sous-jacent.

- Interdire les modifications vers le Store à l’exception d’un groupe d’utilisateurs qui sont inscrits dans une base de données distincte. Pour d’autres utilisateurs, le schéma et le modèle sont en lecture seule.

- Interdire les modifications du modèle si une propriété booléenne du diagramme est définie sur true. Fournir une commande de menu pour modifier cette propriété. Cela permet de garantir aux utilisateurs qui ils n’effectuent pas modifie accidentellement.

- Interdire l’ajout et suppression d’éléments et les relations de classes particuliers, mais autoriser les modifications de propriété. Cela fournit aux utilisateurs un formulaire fixe dans lequel ils peuvent entrer les propriétés.

## <a name="lock-values"></a>Valeurs de verrouillage
 Verrous peuvent être définies sur un Store, une Partition ou un ModelElement individuel. Verrous est un `Flags` énumération : vous pouvez combiner ses valeurs à l’aide de «&#124;».

- Verrous d’un ModelElement toujours incluent les verrous de sa Partition.

- Verrous d’une Partition toujours incluent les verrous du Store.

  Vous ne peut pas définir un verrou sur une partition ou stocker et à la fois désactiver le verrou sur un élément individuel.

|Value|Ce qui signifie que si `IsLocked(Value)` a la valeur true|
|-|-|
|Aucun.|Aucune restriction.|
|Propriété|Propriétés du domaine d’éléments ne peut pas être modifiées. Cela ne s’applique pas aux propriétés qui sont générées par le rôle d’une classe de domaine dans une relation.|
|Ajouter|Nouveaux éléments et liens ne peut pas être créés dans une partition ou stocker.<br /><br /> Non applicable à `ModelElement`.|
|Déplacement|Élément ne peut pas être déplacé entre les partitions si `element.IsLocked(Move)` a la valeur true, ou si `targetPartition.IsLocked(Move)` a la valeur true.|
|Supprimer|Un élément ne peut pas être supprimé si ce verrou est défini sur l’élément lui-même, ou sur un des éléments à laquelle la suppression transmettrait, tels que des formes et des éléments incorporés.<br /><br /> Vous pouvez utiliser `element.CanDelete()` pour découvrir si un élément peut être supprimé.|
|Renouvellement de commande|Impossible de modifier l’ordre des liens à un roleplayer.|
|RolePlayer|L’ensemble de liens qui sont générés à cet élément ne peut pas être modifié. Par exemple, les nouveaux éléments ne peut pas être incorporés sous cet élément. Cela n’affecte pas les liens pour lequel cet élément est la cible.<br /><br /> Si cet élément est un lien, sa source et la cible ne sont pas affectés.|
|Tous|De bits OR sur les autres valeurs.|

## <a name="locking-policies"></a>Stratégies de verrouillage
 En tant qu’auteur d’un DSL, vous pouvez définir un *stratégie de verrouillage*. Une stratégie de verrouillage modère l’opération de SetLocks(), afin que vous pouvez empêcher des verrous spécifiques d’être définie ou imposer que les verrous spécifiques doivent être définies. En règle générale, vous utiliseriez une stratégie de verrouillage afin d’empêcher les utilisateurs ou les développeurs de contravening accidentellement l’utilisation prévue d’une solution DSL, de la même manière que vous pouvez déclarer une variable `private`.

 Vous pouvez également utiliser une stratégie de verrouillage pour définir des verrous sur tous les éléments dépendants sur le type de l’élément. Il s’agit, car `SetLocks(Locks.None)` est toujours appelé quand un élément est tout d’abord créé ou désérialisé à partir du fichier.

 Toutefois, vous ne pouvez pas utiliser une stratégie pour faire varier les verrous sur un élément pendant sa durée de vie. Pour obtenir cet effet, vous devez utiliser des appels à `SetLocks()`.

 Pour définir une stratégie de verrouillage, vous devez :

- Créez une classe qui implémente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Ajouter cette classe pour les services qui sont disponibles via le DocData de votre DSL.

### <a name="to-define-a-locking-policy"></a>Pour définir une stratégie de verrouillage
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> a la définition suivante :

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Ces méthodes sont appelées lorsqu’un appel est effectué à `SetLocks()` sur un Store, une Partition ou un ModelElement. Dans chaque méthode, vous sont fournis avec un ensemble proposé de verrous. Vous pouvez retourner le jeu proposé, ou vous pouvez ajouter et soustraire des verrous.

 Exemple :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 Pour vous assurer que les utilisateurs peuvent toujours supprimer des éléments, même si d’autres appels de code `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Pour interdire les modifications dans toutes les propriétés de chaque élément de MyClass :

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Pour rendre votre stratégie disponibles en tant que service
 Dans votre `DslPackage` de projet, ajoutez un nouveau fichier qui contient le code qui ressemble à l’exemple suivant :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
