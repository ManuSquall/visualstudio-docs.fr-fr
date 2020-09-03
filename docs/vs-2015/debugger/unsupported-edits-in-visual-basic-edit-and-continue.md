---
title: Modifications non prises en charge dans Visual Basic modifier & continuer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155435"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Modifications non prises en charge dans Modifier &amp; Continuer (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifier &amp; Continuer vous permet d'arrêter l'exécution d'un programme en mode Arrêt, d'apporter des modifications à l'exécution de code, puis de continuer l'exécution du programme avec les modifications récemment incorporées. Les modifications de code déclaratif qui affectent la structure publique d'une classe sont interdites, mais de nombreuses modifications que vous pouvez apporter à une méthode, au corps d'une propriété ou à des déclarations privées dans une classe sont autorisées.  
  
 Si vous devez effectuer une modification qui n'est pas prise en charge, arrêtez le débogage, procédez aux modifications et démarrez une nouvelle session de débogage.  
  
### <a name="method-and-property-body-edits"></a><a name="BKMK_MethodandPropertyBodyEdits"></a> Modifications du corps de la méthode et de la propriété  
 **Modifications non prises en charge pour les variables locales statiques**: ajout ou mise à jour d’une variable locale, ou suppression d’une variable locale statique si cela provoque une erreur de compilation.  
  
 **Modifications non prises en charge dans les génériques**: les modifications apportées à la méthode générique elle-même ou au corps de méthode générique ne sont pas prises en charge. L'instanciation d'un type générique ou les appels aux méthodes génériques existantes peuvent être ajoutés, supprimés ou modifiés.  
  
 **Autres modifications non prises en charge**  
  
- Modification de l'instruction d'appel d'une méthode située sur la pile des appels.  
  
- Ajout d'un bloc `Try...Catch`, lorsque le pointeur d'instruction finit dans le bloc `Catch` ou le bloc `Finally`.  
  
- Suppression d’un `Try...Catch` bloc, lorsque le pointeur d’instruction se trouve dans un `Catch` bloc ou dans le `Finally` bloc.  
  
- Ajout d'un bloc `Using` autour du pointeur d'instruction en cours.  
  
- Ajout d'un bloc `SynchLock` autour du pointeur d'instruction en cours.  
  
### <a name="attribute-edits"></a><a name="BKMK_AttributeEdits"></a> Modifications d’attributs  
 Modifier &amp; Continuer ne prend pas en charge la modification d'attributs. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- définition, modification ou suppression d'une classe d'attributs ;  
  
- ajout d'un attribut ;  
  
- modification ou suppression d'un attribut.  
  
### <a name="class-declaration-edits"></a><a name="BKMK_ClassDeclarationEdits"></a> Modifications de déclaration de classe  
 La plupart des modifications apportées aux déclarations de classe ne sont pas autorisées par Modifier &amp; Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Attribution d'un nouveau nom, suppression ou modification de l'héritage d'une classe existante.  
  
- Implémentation d'une nouvelle interface ou suppression de l'implémentation d'une interface.  
  
- Modification de modificateurs sur une classe.  
  
- Ajout, modification ou suppression de l'état `ComClass`.  
  
- Modification d'une déclaration de classe générique.  
  
### <a name="class-member-declaration-edits"></a><a name="BKMK_ClassMemberDeclarationEdits"></a> Modifications de déclaration de membre de classe  
 Les modifications apportées aux déclarations de membre sont interdites dans la plupart des cas de type Modifier &amp; Continuer. Par exemple, vous ne pouvez pas modifier la signature ni le niveau d'accès d'un membre, et vous ne pouvez pas supprimer complètement des membres si cela entraîne une erreur de compilation. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Occultation d'une variable membre existante en déclarant une variable globale ou membre du même nom dans le bloc conteneur.  
  
- Occultation d'une variable locale statique en déclarant une nouvelle instance à l'intérieur d'un bloc.  
  
- Suppression de gestionnaires pour un événement. L'ajout d'un gestionnaire d'événements est autorisé.  
  
- Ajout d'une nouvelle propriété ou méthode de surcharge, à moins que la propriété ou méthode ne soit `Private` et qu'il n'y ait pas d'occurrences du nom dans une instruction active.  
  
- Ajout ou suppression de la clause `WithEvents` sur une variable membre.  
  
- Suppression d'un membre.  
  
- Modification d'une déclaration de propriété ou de méthode pour arrêter l'implémentation d'une interface.  
  
- Modification de toute méthode qui utilise des génériques.  
  
- Modification de la signature ou du type de retour d’une propriété ou méthode non privée.  
  
- Substitution ou occultation d'un membre dans une classe de base.  
  
- Ajout d'un nouveau champ dans une classe quelconque marquée avec `SequentialLayout` ou `ExplicitLayout`.  
  
- Modification de l'état `MustInherit` ou `NotOverridable` d'une méthode.  
  
- Modification des modificateurs d’accès pour une propriété ou méthode.  
  
- Modification du type ou de l'état en lecture seule d'un champ.  
  
- Modification d'un champ public.  
  
### <a name="compiler-option-edits"></a><a name="BKMK_CompilerOptionEdits"></a> Modifications des options du compilateur  
 En utilisant Modifier &amp; Continuer en mode arrêt, vous ne pouvez pas changer, ajouter ou supprimer les options de compilateur suivantes :  
  
- **Option Strict**  
  
- **Option Explicit**  
  
- **Option Compare**  
  
### <a name="constants-edits"></a><a name="BKMK_ConstantsEdits"></a> Modifications des constantes  
 Les modifications des constantes en mode Modifier &amp; Continuer sont très limitées. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Ajout ou mise à jour d'une variable constante.  
  
- Modification du type ou de la valeur d'une constante.  
  
- Suppression d'une constante.  
  
### <a name="delegate-and-event-declaration-edits"></a><a name="BKMK_DelegateandEventDeclarationEdits"></a> Modifications relatives aux déclarations Delegate et Event  
 Certaines modifications apportées aux délégués et aux événements ne sont pas autorisées par Modifier &amp; Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Changement ou suppression d'une définition de délégué.  
  
- Suppression d'un événement.  
  
### <a name="enumeration-edits"></a><a name="BKMK_EnumerationEdits"></a> Modifications d’énumération  
 Les modifications apportées aux énumérations (`Enums`) ne sont pas autorisées par Modifier &amp; Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Modification du type sous-jacent d'un `Enum`.  
  
- Ajout, changement ou suppression d'un membre `Enum`.  
  
- Modification du modificateur d’accès d’un `Enum`.  
  
### <a name="external-declarations-edits"></a><a name="BKMK_ExternalDeclarationsEdits"></a> Modifications des déclarations externes  
 En général, vous ne pouvez pas modifier les déclarations de méthodes externes pendant Modifier &amp; Continuer. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Ajout ou suppression d'une déclaration externe.  
  
- Modification de la signature ou des attributs de marshaling d'une déclaration externe.  
  
### <a name="imports-edits"></a><a name="BKMK_ImportsEdits"></a> Modifications des importations  
 Modifier &amp; Continuer n'autorise pas l'ajout, le changement ou la suppression d'instructions `Imports` en mode Arrêt.  
  
### <a name="interface-definition-edits"></a><a name="BKMK_InterfaceDefinitionEdits"></a> Modifications de la définition d’interface  
 Bien que vous soyez fréquemment autorisés à apporter des modifications aux membres qui implémentent des interfaces, les modifications aux définitions d'interface ne sont pas autorisées en général par Modifier et Continuer. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Ajout, modification ou suppression de membres d'interface.  
  
- Suppression d'une interface existante.  
  
- Modification du modificateur d’accès d’une interface.  
  
- Modification de la hiérarchie d'héritage de l'interface.  
  
### <a name="module-declaration-edits"></a><a name="BKMK_ModuleDeclarationEdits"></a> Modifications de déclaration de module  
 La plupart des modifications aux déclarations de module ne sont pas autorisées par Modifier &amp; Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Création d'un nouveau module.  
  
- Attribution d'un nouveau nom ou suppression d'un module existant.  
  
- Modification du modificateur d’accès d’un module.  
  
### <a name="module-member-declaration-edits"></a><a name="BKMK_ModuleMemberDeclarationEdits"></a> Modifications de déclaration de membre de module  
 À l'aide de Modifier &amp; Continuer, vous pouvez apporter différentes modifications aux membres de module, tels que propriétés, méthodes et champs, en mode Arrêt. Certaines modifications ne sont toutefois pas prises en charge. Plus particulièrement, Modifier &amp; Continuer ne prend pas en charge l'ajout, la suppression ni la modification du type ou de la signature de membres quelconques.  
  
 En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Ajout d'un nouveau membre à moins qu'il n'existe pas d'occurrence de ce nom dans une quelconque instruction active.  
  
- Suppression d'une propriété ou méthode.  
  
- Modification de la signature d'une propriété ou d'une méthode.  
  
- Ajout, modification du nom, déplacement ou suppression d'un champ.  
  
- Modification de toute méthode qui utilise des génériques.  
  
- Modification des modificateurs d'accès d'une propriété ou d'une méthode, par exemple, remplacer `Public` par `Private`.  
  
- Suppression ou modification du type d'un champ existant.  
  
### <a name="nested-type-declaration-edits"></a><a name="BKMK_NestedTypeDeclarationEdits"></a> Modifications de déclaration de type imbriqué  
 Modifier &amp; Continuer ne prend pas en charge le déplacement d'un type imbriqué vers un autre espace de noms ou type.  
  
### <a name="structure-declaration-edits"></a><a name="BKMK_StructureDeclarationEdits"></a> Modifications de déclaration de structure  
 La plupart des modifications apportées aux déclarations de structure ne sont pas autorisées par modifier & Continuer en mode **arrêt** . En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Attribution d'un nouveau nom ou suppression d'une structure existante.  
  
- Implémentation d'une nouvelle interface ou suppression de l'implémentation d'une interface.  
  
- Modification du modificateur d'accès d'une structure.  
  
### <a name="structure-member-declaration-edits"></a><a name="BKMK_StructureMemberDeclarationEdits"></a> Modifications de déclaration de membre de structure  
 À l'aide de Modifier &amp; Continuer, vous pouvez apporter différentes modifications aux membres de structure (propriétés, méthodes et champs) en mode Arrêt. Toutefois, certaines modifications ne sont pas prises en charge, en particulier celles qui affectent la déclaration de membres de structure. En particulier, la fonctionnalité Modifier &amp; Continuer ne prend pas en charge les modifications suivantes :  
  
- Suppression d'une propriété ou méthode.  
  
- Ajout ou suppression d'un champ.  
  
- Modification de la signature d'une propriété ou d'une méthode.  
  
- Modification de toute méthode qui utilise des génériques.  
  
- Sélection d'une déclaration de propriété ou de méthode pour implémenter une interface.  
  
- Modification des modificateurs d’accès d’une propriété ou d’une méthode (par exemple, modification `Public` en **privé**).  
  
- Suppression d'un champ.  
  
- Modification d'un type de champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : appliquer des modifications en mode arrêt avec modifier & continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Modifier &amp; Continuer (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
