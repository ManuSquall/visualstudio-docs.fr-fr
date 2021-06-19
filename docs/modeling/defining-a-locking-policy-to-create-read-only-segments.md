---
title: Définition d'une stratégie de verrouillage pour créer des segments en lecture seule
description: Découvrez comment vous pouvez définir une stratégie pour un programme afin de verrouiller tout ou partie d’un modèle de langage spécifique à un domaine (DSL) afin qu’il puisse être lu mais pas modifié.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385784"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Définition d'une stratégie de verrouillage pour créer des segments en lecture seule
L’API d’immuabilité du kit de développement logiciel (SDK) de visualisation et de modélisation de Visual Studio permet à un programme de verrouiller tout ou partie d’un modèle de langage spécifique à un domaine (DSL) afin qu’il puisse être lu mais pas modifié. Cette option en lecture seule peut être utilisée, par exemple, pour qu’un utilisateur puisse demander aux collègues d’annoter et de passer en revue un modèle DSL, mais peut les empêcher de modifier l’original.

 En outre, en tant qu’auteur d’une solution DSL, vous pouvez définir une *stratégie de verrouillage.* Une stratégie de verrouillage définit les verrous autorisés, non autorisés ou obligatoires. Par exemple, lorsque vous publiez un DSL, vous pouvez encourager les développeurs tiers à l’étendre avec de nouvelles commandes. Toutefois, vous pouvez également utiliser une stratégie de verrouillage pour les empêcher de modifier l’État en lecture seule des parties spécifiées du modèle.

> [!NOTE]
> Une stratégie de verrouillage peut être contournée à l’aide de la réflexion. Il fournit une limite claire pour les développeurs tiers, mais ne fournit pas une sécurité renforcée.

 Des informations supplémentaires et des exemples sont disponibles sur le site Web du [Kit de développement logiciel de visualisation et de modélisation](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) de Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Définition et obtention de verrous
 Vous pouvez définir des verrous sur le magasin, sur une partition ou sur un élément individuel. Par exemple, cette instruction empêchera la suppression d’un élément de modèle, et empêchera également la modification de ses propriétés :

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 D’autres valeurs de verrouillage peuvent être utilisées pour empêcher les modifications de relations, la création d’éléments, le déplacement entre les partitions et la réorganisation des liens dans un rôle.

 Les verrous s’appliquent aux actions de l’utilisateur et au code du programme. Si le code de programme tente d’apporter une modification, une `InvalidOperationException` est levée. Les verrous sont ignorés lors d’une opération d’annulation ou de rétablissement.

 Vous pouvez déterminer si un élément a un verrou dans un jeu donné à l’aide de `IsLocked(Locks)` et que vous pouvez obtenir le jeu actuel de verrous sur un élément à l’aide de `GetLocks()` .

 Vous pouvez définir un verrou sans utiliser de transaction. Le verrou de base de données ne fait pas partie du magasin. Si vous définissez un verrou en réponse à une modification d’une valeur dans le magasin, par exemple dans OnValueChanged, vous devez autoriser les modifications qui font partie d’une opération d’annulation.

 Ces méthodes sont des méthodes d’extension définies dans l' <xref:Microsoft.VisualStudio.Modeling.Immutability> espace de noms.

### <a name="locks-on-partitions-and-stores"></a>Verrous sur les partitions et les magasins
 Les verrous peuvent également être appliqués aux partitions et au magasin. Un verrou défini sur une partition s’applique à tous les éléments de la partition. Par exemple, l’instruction suivante empêchera tous les éléments d’une partition d’être supprimés, quels que soient les États de leurs propres verrous. Toutefois, d’autres verrous tels que `Locks.Property` peuvent toujours être définis sur des éléments individuels :

```csharp
partition.SetLocks(Locks.Delete);
```

 Un verrou défini sur le magasin s’applique à tous ses éléments, quels que soient les paramètres de ce verrou sur les partitions et les éléments.

### <a name="using-locks"></a>Utilisation de verrous
 Vous pouvez utiliser des verrous pour implémenter des schémas tels que les exemples suivants :

- Interdisez les modifications apportées à tous les éléments et relations, à l’exception de ceux qui représentent des commentaires. Cela permet aux utilisateurs d’annoter un modèle sans le modifier.

- Interdire les modifications dans la partition par défaut, mais autoriser les modifications dans la partition du diagramme. L’utilisateur peut réorganiser le diagramme, mais ne peut pas modifier le modèle sous-jacent.

- Interdire les modifications apportées au magasin, à l’exception d’un groupe d’utilisateurs inscrits dans une base de données distincte. Pour les autres utilisateurs, le schéma et le modèle sont en lecture seule.

- Interdire les modifications apportées au modèle si une propriété booléenne du diagramme a la valeur true. Fournissez une commande de menu pour modifier cette propriété. Cela permet de garantir que les utilisateurs ne peuvent pas apporter de modifications accidentelles.

- Interdire l’ajout et la suppression d’éléments et de relations de classes particulières, mais autoriser les modifications de propriété. Cela fournit aux utilisateurs une forme fixe dans laquelle ils peuvent remplir les propriétés.

## <a name="lock-values"></a>Valeurs de verrouillage
 Les verrous peuvent être définis sur un magasin, une partition ou un ModelElement individuel. Les verrous sont une `Flags` énumération : vous pouvez combiner ses valeurs à l’aide de' &#124; '.

- Les verrous d’un ModelElement incluent toujours les verrous de sa partition.

- Les verrous d’une partition incluent toujours les verrous du magasin.

  Vous ne pouvez pas définir un verrou sur une partition ou un magasin et désactiver en même temps le verrou sur un élément individuel.

|Valeur|Cela signifie que si `IsLocked(Value)` a la valeur true|
|-|-|
|Aucun|Aucune restriction.|
|Propriété|Les propriétés de domaine des éléments ne peuvent pas être modifiées. Cela ne s’applique pas aux propriétés générées par le rôle d’une classe de domaine dans une relation.|
|Ajouter|Impossible de créer des éléments et des liens dans une partition ou un magasin.<br /><br /> Non applicable à `ModelElement` .|
|Déplacer|L’élément ne peut pas être déplacé entre des partitions si `element.IsLocked(Move)` a la valeur true, ou si `targetPartition.IsLocked(Move)` a la valeur true.|
|DELETE|Un élément ne peut pas être supprimé si ce verrou est défini sur l’élément lui-même, ou sur l’un des éléments dans lequel la suppression se propage, comme des éléments et des formes incorporés.<br /><br /> Vous pouvez utiliser `element.CanDelete()` pour déterminer si un élément peut être supprimé.|
|Réorganiser|L’ordre des liens au niveau d’un rolePlayer ne peut pas être modifié.|
|RolePlayer|L’ensemble de liens qui sont associés à cet élément ne peut pas être modifié. Par exemple, les nouveaux éléments ne peuvent pas être incorporés sous cet élément. Cela n’affecte pas les liens pour lesquels cet élément est la cible.<br /><br /> Si cet élément est un lien, sa source et sa cible ne sont pas affectées.|
|Tous|Or au niveau du bit des autres valeurs.|

## <a name="locking-policies"></a>Stratégies de verrouillage
 En tant qu’auteur d’une solution DSL, vous pouvez définir une *stratégie de verrouillage*. Une stratégie de verrouillage permet de modérer le fonctionnement de SetLocks (), afin que vous puissiez empêcher des verrous spécifiques d’être définis ou d’imposer que des verrous spécifiques soient définis. En règle générale, vous utilisez une stratégie de verrouillage pour dissuader les utilisateurs ou les développeurs de transgresser accidentellement l’utilisation prévue d’un DSL, de la même manière que vous pouvez déclarer une variable `private` .

 Vous pouvez également utiliser une stratégie de verrouillage pour définir des verrous sur tous les éléments qui dépendent du type de l’élément. Cela est dû `SetLocks(Locks.None)` au fait que est toujours appelé lorsqu’un élément est créé ou désérialisé pour la première fois à partir d’un fichier.

 Toutefois, vous ne pouvez pas utiliser une stratégie pour faire varier les verrous sur un élément pendant sa durée de vie. Pour obtenir cet effet, vous devez utiliser des appels à `SetLocks()` .

 Pour définir une stratégie de verrouillage, vous devez :

- Créez une classe qui implémente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Ajoutez cette classe aux services disponibles via le DocData de votre DSL.

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

 Ces méthodes sont appelées lorsqu’un appel est effectué à `SetLocks()` sur un magasin, une partition ou un ModelElement. Dans chaque méthode, vous disposez d’un ensemble de verrous proposés. Vous pouvez retourner l’ensemble proposé, ou vous pouvez ajouter et soustraire des verrous.

 Exemple :

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

 Pour interdire la modification de toutes les propriétés de chaque élément de MyClass :

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Pour rendre votre stratégie disponible en tant que service
 Dans votre `DslPackage` projet, ajoutez un nouveau fichier qui contient le code qui ressemble à l’exemple suivant :

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
