---
title: "D&#233;finition d&#39;une strat&#233;gie de verrouillage pour cr&#233;er des segments en lecture seule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 12
---
# D&#233;finition d&#39;une strat&#233;gie de verrouillage pour cr&#233;er des segments en lecture seule
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'API d'immuabilité du Kit de développement logiciel de visualisation et de modélisation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet à un programme à la pièce de verrou ou tout le modèle de langage \(DSL\) spécifique au domaine afin qu'elle puisse être lue mais non modifié.  Cette option en lecture seule peut être utilisé, par exemple, afin qu'un utilisateur puisse demander à vos collègues d'annoter et l'examen d'un modèle DÉSOLÉ mais peut les empêcher de modifier l'original.  
  
 En outre, comme auteur d'un DÉSOLÉ, vous pouvez définir *une stratégie verrouillante.* Une stratégie verrouillante définit que les verrous sont autorisé, pas autorisée, ou de liaison.  Par exemple, lorsque vous publiez un langage spécifique à un domaine, vous pouvez encourager les développeurs tiers à l'étendre avec de nouvelles commandes.  Mais vous pouvez également utiliser une stratégie verrouillante pour les empêcher de modifier l'état de lecture seule de parties spécifiées de modèle.  
  
> [!NOTE]
>  Une stratégie verrouillante peut être évitée en utilisant la réflexion.  Elle fournit une limite claire pour les développeurs tiers, mais ne fournit pas la sécurité renforcée.  
  
 Plus d'informations et d'exemples sont disponibles sur le site[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) Web de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Définition et obtention de les verrous  
 Vous pouvez définir des verrous sur le magasin, sur une partition, ou sur un élément individuel.  Par exemple, cette instruction empêché un élément de modèle d'être supprimé, et empêché également ses propriétés d'être modifiée :  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 D'autres valeurs de verrou peut être utilisées pour empêcher les modifications des relations, la création d'élément, déplacement entre les partitions, et retrier plusieurs liens à un rôle.  
  
 Les verrous s'appliquent aux actions utilisateur et du code du programme.  Si une application tente de code du programme d'apporter une modification, `InvalidOperationException` sera levée.  Les verrous sont ignorés dans une opération d'annulation ou de rétablissement.  
  
 Vous pouvez déterminer si un élément a un tout verrou dans un ensemble donné à l'aide de `IsLocked(Locks)` et vous pouvez obtenir le actuel de verrous sur un élément à l'aide de `GetLocks()`.  
  
 vous pouvez définir un verrou sans utiliser une transaction.  La base de données de verrou n'est pas partie du magasin.  Si vous définissez un verrou en réponse à une modification dans une valeur de le magasin, par exemple dans OnValueChanged, vous autorisez les modifications qui font partie d'une opération d'annulation.  
  
 Ces méthodes sont des méthodes d'extension définies dans l'espace de noms d' <xref:Microsoft.VisualStudio.Modeling.Immutability> .  
  
### Verrouillages sur les partitions et des magasins  
 Les verrous peuvent également être appliqués à des partitions et au magasin.  Un verrou qui est défini sur une partition s'applique à tous les éléments de la partition.  Par conséquent, par exemple, l'instruction suivante empêché tous les éléments d'une partition d'être supprimé, indépendamment des rapports de leurs propres verrous.  Toutefois, d'autres verrous tels qu' `Locks.Property` peuvent encore être définis sur des éléments :  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un verrou qui est défini sur le magasin s'applique à tous ses éléments, indépendamment des paramètres de ce verrou sur les partitions et les éléments.  
  
### À l'aide de verrous  
 Vous pouvez utiliser des verrous pour implémenter des modèles telles que les exemples suivants :  
  
-   Éliminez les modifications apportées à tous les éléments et les relations excepté ceux qui représentent des commentaires.  Cela permet aux utilisateurs pour annoter un modèle sans le modifier.  
  
-   Éliminez les modifications de la partition par défaut, mais laissez les modifications de la partition du diagramme.  L'utilisateur peut organiser le diagramme, mais ne peut pas modifier le modèle sous\-jacent.  
  
-   Éliminez les modifications au magasin à l'exception d'un groupe d'utilisateurs qui sont stockés dans une base de données différente.  pour d'autres utilisateurs, le diagramme et le modèle sont en lecture seule.  
  
-   Éliminez les modifications apportées au modèle si une propriété booléenne du diagramme a la valeur true.  Fournissez une commande de menu pour modifier cette propriété.  Cela permet de garantir les utilisateurs qu'ils ne s'affichent pas aux modifications par erreur.  
  
-   Éliminez l'ajout et la suppression des éléments et les relations des classes spécifiques, mais laissez les modifications de propriété.  Cela fournit aux utilisateurs un à format fixe dans ce qu'ils peuvent remplir les propriétés.  
  
## Valeurs de verrouillage  
 Les verrous peuvent être définis sur un magasin, une partition, ou un ModelElement individuel.  les verrous est une énumération d' `Flags` : vous pouvez combiner ses valeurs en utilisant « &#124; ».  
  
-   Les verrous d'un ModelElement incluent toujours les verrous de sa partition.  
  
-   Les verrous d'une partition incluent toujours les verrous du magasin.  
  
 Vous ne pouvez pas définir un verrou sur une partition ou stocker et en même temps supprimer le verrouillage un élément individuel.  
  
|Valeur|C'est\-à\-dire si `IsLocked(Value)` a la valeur true|  
|------------|----------------------------------------------------------|  
|Aucun|aucune restriction.|  
|Propriété|Les propriétés de champ des éléments ne peuvent pas être modifiées.  Cela ne s'applique pas aux propriétés qui sont générées par le rôle d'une classe de domaine dans une relation.|  
|Ajouter|De nouveaux éléments et liens ne peuvent pas être créés dans une partition ou un magasin.<br /><br /> non applicable à `ModelElement`.|  
|Déplacement|L'élément ne peut pas être déplacé entre les partitions si `element.IsLocked(Move)` est vraie, ou si `targetPartition.IsLocked(Move)` est true.|  
|Supprimer|Un élément ne peut pas être supprimé si ce verrou est défini sur l'élément lui\-même, ou sur l'un des éléments auxquels la suppression propage, comme les éléments incorporés et les formes.<br /><br /> Vous pouvez utiliser `element.CanDelete()` pour déterminer si un élément peut être supprimé.|  
|Réoganiser|classer des liens à un roleplayer ne peut pas être modifié.|  
|RolePlayer|L'ensemble de liens qui sont générés à cet élément ne peut pas être modifié.  Par exemple, les nouveaux éléments ne peuvent pas être incorporés dans cet élément.  Cela n'affecte pas les liens pour lesquels cet élément est la cible.<br /><br /> si cet élément est un lien, sa source et cible ne sont pas affectées.|  
|Tous|Opération de bits OR des autres valeurs.|  
  
## Stratégies de verrouillage  
 En tant qu'auteur d'un langage spécifique à un domaine, vous pouvez définir *une stratégie verrouillante*.  Une stratégie verrouillante modère l'opération de SetLocks\(\), afin que vous puissiez empêcher les verrous spécifiques d'être défini ou exiger que les verrouillages spécifiques doivent être définis.  En général, vous utiliserez une stratégie verrouillante pour décourager des utilisateurs ou des développeurs de violer accidentellement l'utilisation prévue d'un langage spécifique à un domaine, de la même façon que vous pouvez déclarer `private`variable.  
  
 Vous pouvez également utiliser une stratégie verrouillante pour définir des verrous sur tous les éléments dépendants sur le type d'élément.  En effet `SetLocks(Locks.None)` est toujours appelé lorsqu'un élément est créée pour la première fois ou désérialisé du fichier.  
  
 Toutefois, vous ne pouvez pas utiliser une stratégie pour faire varier les verrouillages sur un élément pendant sa vie.  Pour accomplir cette fin, vous devez utiliser les appels à `SetLocks()`.  
  
 pour définir une stratégie verrouillante, vous devez :  
  
-   créez une classe qui implémente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Ajoutez cette classe aux services disponibles via le DocData de votre DÉSOLÉ.  
  
### pour définir une stratégie verrouillante  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> est défini comme suit :  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Ces méthodes sont appelées lorsqu'un appel est fait à `SetLocks()` sur un magasin, une partition, ou un ModelElement.  Dans chaque méthode, vous êtes instrumenté d'ensemble proposé de verrous.  Vous pouvez retourner tout proposé, ou vous pouvez ajouter et supprimer des verrous.  
  
 Par exemple :  
  
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
  
 Pour vous assurer que les utilisateurs peuvent toujours supprimer des éléments, même si un autre code appelle `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Pour empêcher la modification de toutes les propriétés de chaque élément de MyClass :  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### pour définir votre stratégie disponible en tant que service  
 Dans votre projet d' `DslPackage` , ajoutez un nouveau fichier qui contient le code qui ressemble à l'exemple suivant :  
  
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