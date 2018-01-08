---
title: "Définition d’une stratégie de verrouillage pour créer des Segments en lecture seule | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: "12"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 93e4393a7b6731a10a00dc309353dba5870c269f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Définition d'une stratégie de verrouillage pour créer des segments en lecture seule
L’API immuabilité de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK permet à un programme à tout ou partie de verrouillage d’un modèle de langage de spécifique à un domaine (DSL) afin qu’elle peut être lue mais pas modifié. Cette option en lecture seule peut être utilisée, par exemple, afin qu’un utilisateur peut demander à vos collègues à annoter et passez en revue un modèle DSL, mais il peut ne pas autoriser les à partir de la modification de l’original.  
  
 En outre, en tant qu’auteur du DSL, vous pouvez définir un *stratégie de verrouillage.* Une stratégie de verrouillage définit quels verrous sont autorisées, non autorisé ou obligatoire. Par exemple, lorsque vous publiez une DSL, vous pouvez encourager les développeurs tiers pour l’étendre avec de nouvelles commandes. Mais vous pouvez également utiliser une stratégie de verrouillage pour empêcher toute modification de l’état en lecture seule des parties spécifiées du modèle.  
  
> [!NOTE]
>  Une stratégie de verrouillage peut être contournée en utilisant la réflexion. Il fournit une limite pour les développeurs tiers, mais ne fournit pas de sécurité renforcée.  
  
 Plus d’informations et des exemples sont disponibles sur le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) site Web.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>Définition et l’obtention des verrous  
 Vous pouvez définir des verrous sur la banque, sur une partition ou sur un élément individuel. Par exemple, cette instruction empêche un élément de modèle de suppression et également empêche ses propriétés en cours de modification :  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Autres valeurs de verrou peuvent être utilisées pour empêcher la modification de relations, de création d’éléments, de mouvement entre les partitions et les liens nouveau classement dans un rôle.  
  
 Les verrous s’appliquent aux actions de l’utilisateur et au code de programme. Si le code de programme tente d’apporter une modification, une `InvalidOperationException` sera levée. Les verrous sont ignorés dans une opération d’annulation ou de restauration par progression.  
  
 Vous pouvez détecter si un élément a un verrou quelconque dans un jeu donné à l’aide de `IsLocked(Locks)` et vous pouvez obtenir l’ensemble actuel de verrous sur un élément à l’aide de `GetLocks()`.  
  
 Vous pouvez définir un verrou sans l’aide d’une transaction. La base de données de verrou n’est pas partie de la banque. Si vous définissez un verrou en réponse à une modification d’une valeur dans le magasin, par exemple dans OnValueChanged, vous devez autoriser les modifications qui font partie d’une opération d’annulation.  
  
 Ces méthodes sont des méthodes d’extension qui sont définies dans le <xref:Microsoft.VisualStudio.Modeling.Immutability> espace de noms.  
  
### <a name="locks-on-partitions-and-stores"></a>Verrous de partitions et de magasins  
 Verrous peuvent également être appliqués aux partitions et le magasin. Un verrou qui est défini sur une partition s’applique à tous les éléments dans la partition. Par conséquent, par exemple, l’instruction suivante empêche tous les éléments d’une partition en cours de suppression, quelles que soient les États de leurs verrous. Toutefois, d’autres verrous comme `Locks.Property` peut toujours être définies sur les éléments individuels :  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un verrou qui est défini sur la banque s’applique à tous ses éléments, quels que soient les paramètres de ce verrou sur les partitions et les éléments.  
  
### <a name="using-locks"></a>L’utilisation de verrous  
 Vous pouvez utiliser des verrous pour implémenter les méthodes telles que les exemples suivants :  
  
-   Ne pas autoriser les modifications apportées à tous les éléments et des relations à l’exception de ceux qui représentent des commentaires. Cela permet aux utilisateurs d’annoter un modèle sans le modifier.  
  
-   Interdire les modifications apportées à la partition par défaut, mais autoriser les modifications dans la partition de schéma. L’utilisateur peut réorganiser le diagramme, mais vous ne pouvez pas modifier le modèle sous-jacent.  
  
-   Ne pas autoriser les modifications dans le magasin, à l’exception d’un groupe d’utilisateurs qui sont inscrits dans une base de données distincte. Pour d’autres utilisateurs, le diagramme et le modèle sont en lecture seule.  
  
-   Interdire les modifications du modèle si une propriété booléenne du diagramme est définie sur true. Fournir une commande de menu pour modifier cette propriété. Cela permet de garantir des utilisateurs qu’ils n’apportez pas de modifications par inadvertance.  
  
-   Interdire l’ajout et suppression d’éléments et les relations des catégories spécifiques, mais autorise les modifications de propriété. Cela fournit aux utilisateurs un formulaire fixe dans lequel ils peuvent remplir les propriétés.  
  
## <a name="lock-values"></a>Valeurs de verrou  
 Verrous peuvent être définies sur un magasin, une Partition ou un ModelElement individuel. Verrous est un `Flags` énumération : vous pouvez combiner ses valeurs à l’aide de ' &#124;'.  
  
-   Les verrous d’un ModelElement toujours incluent les verrous de sa Partition.  
  
-   Les verrous d’une Partition toujours incluent les verrous de la banque.  
  
 Vous ne pouvez pas défini un verrou sur une partition ou de stocker et en même temps, désactiver le verrou sur un élément individuel.  
  
|Value|Ce qui signifie que si `IsLocked(Value)` a la valeur true|  
|-----------|------------------------------------------|  
|Aucun.|Aucune restriction.|  
|Propriété|Propriétés du domaine d’éléments ne peut pas être modifiées. Cela ne s’applique pas aux propriétés qui sont générées par le rôle d’une classe de domaine dans une relation.|  
|Ajouter|Nouveaux éléments et les liens ne peut pas être créés dans une partition ou à stocker.<br /><br /> Non applicable à `ModelElement`.|  
|Déplacement|Élément ne peut pas être déplacé entre des partitions si `element.IsLocked(Move)` a la valeur true, ou si `targetPartition.IsLocked(Move)` a la valeur true.|  
|Supprimer|Un élément ne peut pas être supprimé si ce verrou est défini sur l’élément lui-même, ou sur un des éléments à laquelle la suppression transmettrait, tels que les formes et les éléments incorporés.<br /><br /> Vous pouvez utiliser `element.CanDelete()` pour détecter si un élément peut être supprimé.|  
|Réorganiser les|L’ordre des liens à un roleplayer ne peut pas être modifié.|  
|RolePlayer|L’ensemble de liens qui sont générés à cet élément ne peut pas être modifié. Par exemple, les nouveaux éléments ne peut pas être incorporés sous cet élément. Cela n’affecte pas les liens pour laquelle cet élément est la cible.<br /><br /> Si cet élément est un lien, sa source et la cible ne sont pas affectées.|  
|Tous|De bits OR sur les autres valeurs.|  
  
## <a name="locking-policies"></a>Stratégies de verrouillage  
 En tant qu’auteur du DSL, vous pouvez définir un *stratégie de verrouillage*. Une stratégie de verrouillage modère le fonctionnement de SetLocks(), afin que vous pouvez empêcher verrous spécifiques définir ou d’imposer que les verrous spécifiques doivent être définies. En règle générale, vous utiliseriez une stratégie de verrouillage afin d’empêcher les utilisateurs ou les développeurs d’accidentellement contravening l’utilisation prévue de DSL, de la même manière que vous pouvez déclarer une variable `private`.  
  
 Vous pouvez également utiliser une stratégie de verrouillage pour définir des verrous sur tous les éléments dépendants sur le type de l’élément. C’est parce que `SetLocks(Locks.None)` est toujours appelé quand un élément est tout d’abord créé ou désérialisé à partir du fichier.  
  
 Toutefois, vous ne pouvez pas utiliser une stratégie pour faire varier les verrous sur un élément pendant sa durée de vie. Pour obtenir cet effet, vous devez utiliser les appels à `SetLocks()`.  
  
 Pour définir une stratégie de verrouillage, vous devez :  
  
-   Créez une classe qui implémente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Ajouter cette classe pour les services qui sont disponibles via le DocData de votre DSL.  
  
### <a name="to-define-a-locking-policy"></a>Pour définir une stratégie de verrouillage  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>a la définition suivante :  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Ces méthodes sont appelées lorsqu’un appel est effectué à `SetLocks()` sur un magasin, une Partition ou un ModelElement. Dans chaque méthode, vous sont fournies avec un ensemble proposé de verrous. Vous pouvez retourner le jeu proposé, ou vous pouvez ajouter et soustraire des verrous.  
  
 Exemple :  
  
```  
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
  
 Pour vous assurer que les utilisateurs peuvent toujours supprimer des éléments, même si d’autres appels de code`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Pour interdire les modifications dans toutes les propriétés de chaque élément de MyClass :  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>À la disposition de votre stratégie en tant que service  
 Dans votre `DslPackage` de projet, ajoutez un nouveau fichier qui contient le code qui ressemble à l’exemple suivant :  
  
```  
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
