---
title: Les modifications non prises en charge dans Visual Basic Modifier & Continuer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: bc6e7a5d1d72464849bff20be066ea70e8264623
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787898"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Modifications non prises en charge dans Modifier & Continuer (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifier & Continuer vous permet d'arrêter l'exécution d'un programme en mode Arrêt, d'apporter des modifications à l'exécution de code, puis de continuer l'exécution du programme avec les modifications récemment incorporées. Les modifications de code déclaratif qui affectent la structure publique d'une classe sont interdites, mais de nombreuses modifications que vous pouvez apporter à une méthode, au corps d'une propriété ou à des déclarations privées dans une classe sont autorisées.  
  
 Si vous devez effectuer une modification qui n'est pas prise en charge, arrêtez le débogage, procédez aux modifications et démarrez une nouvelle session de débogage.  
  
###  <a name="BKMK_MethodandPropertyBodyEdits"></a> Méthode et modifications relatives au corps de propriété  
 **Non pris en charge des modifications apportées aux Variables locales statiques**: ajout ou la mise à jour une variable locale ou suppression d’une variable locale statique si cela peut provoquer une erreur de compilation.  
  
 **Non pris en charge des modifications aux génériques**: modifications apportées à la méthode générique elle-même ou le corps de méthode générique ne sont pas pris en charge. L'instanciation d'un type générique ou les appels aux méthodes génériques existantes peuvent être ajoutés, supprimés ou modifiés.  
  
 **Autres modifications non prises en charge**  
  
-   Modification de l'instruction d'appel d'une méthode située sur la pile des appels.  
  
-   Ajout d'un bloc `Try...Catch`, lorsque le pointeur d'instruction finit dans le bloc `Catch` ou le bloc `Finally`.  
  
-   Suppression d’un `Try...Catch` bloc, lorsque le pointeur d’instruction se trouve dans un `Catch`bloc ou le `Finally` bloc.  
  
-   Ajout d'un bloc `Using` autour du pointeur d'instruction en cours.  
  
-   Ajout d'un bloc `SynchLock` autour du pointeur d'instruction en cours.  
  
###  <a name="BKMK_AttributeEdits"></a> Modifications relatives aux attributs  
 Modifier & Continuer ne prend pas en charge la modification d'attributs. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   définition, modification ou suppression d'une classe d'attributs ;  
  
-   ajout d'un attribut ;  
  
-   modification ou suppression d'un attribut.  
  
###  <a name="BKMK_ClassDeclarationEdits"></a> Modifications relatives aux déclarations de classe  
 La plupart des modifications apportées aux déclarations de classe ne sont pas autorisées par Modifier & Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Attribution d'un nouveau nom, suppression ou modification de l'héritage d'une classe existante.  
  
-   Implémentation d'une nouvelle interface ou suppression de l'implémentation d'une interface.  
  
-   Modification de modificateurs sur une classe.  
  
-   Ajout, modification ou suppression de l'état `ComClass`.  
  
-   Modification d'une déclaration de classe générique.  
  
###  <a name="BKMK_ClassMemberDeclarationEdits"></a> Modifications de déclaration de membre de classe  
 Les modifications apportées aux déclarations de membre sont interdites dans la plupart des cas de type Modifier & Continuer. Par exemple, vous ne pouvez pas modifier la signature ni le niveau d'accès d'un membre, et vous ne pouvez pas supprimer complètement des membres si cela entraîne une erreur de compilation. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Occultation d'une variable membre existante en déclarant une variable globale ou membre du même nom dans le bloc conteneur.  
  
-   Occultation d'une variable locale statique en déclarant une nouvelle instance à l'intérieur d'un bloc.  
  
-   Suppression de gestionnaires pour un événement. L'ajout d'un gestionnaire d'événements est autorisé.  
  
-   Ajout d'une nouvelle propriété ou méthode de surcharge, à moins que la propriété ou méthode ne soit `Private` et qu'il n'y ait pas d'occurrences du nom dans une instruction active.  
  
-   Ajout ou suppression de la clause `WithEvents` sur une variable membre.  
  
-   Suppression d'un membre.  
  
-   Modification d'une déclaration de propriété ou de méthode pour arrêter l'implémentation d'une interface.  
  
-   Modification de toute méthode qui utilise des génériques.  
  
-   Modification de la signature ou du type de retour d’une propriété ou méthode non privée.  
  
-   Substitution ou occultation d'un membre dans une classe de base.  
  
-   Ajout d'un nouveau champ dans une classe quelconque marquée avec `SequentialLayout` ou `ExplicitLayout`.  
  
-   Modification de l'état `MustInherit` ou `NotOverridable` d'une méthode.  
  
-   Modification des modificateurs d’accès pour une propriété ou méthode.  
  
-   Modification du type ou de l'état en lecture seule d'un champ.  
  
-   Modification d'un champ public.  
  
###  <a name="BKMK_CompilerOptionEdits"></a> Modifications des options du compilateur  
 En utilisant Modifier & Continuer en mode arrêt, vous ne pouvez pas changer, ajouter ou supprimer les options de compilateur suivantes :  
  
-   **Option Strict**  
  
-   **Option Explicit**  
  
-   **Option Compare**  
  
###  <a name="BKMK_ConstantsEdits"></a> Modifications relatives aux constantes  
 Les modifications des constantes en mode Modifier & Continuer sont très limitées. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Ajout ou mise à jour d'une variable constante.  
  
-   Modification du type ou de la valeur d'une constante.  
  
-   Suppression d'une constante.  
  
###  <a name="BKMK_DelegateandEventDeclarationEdits"></a> Délégué et les modifications de déclaration d’événement  
 Certaines modifications apportées aux délégués et aux événements ne sont pas autorisées par Modifier & Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Changement ou suppression d'une définition de délégué.  
  
-   Suppression d'un événement.  
  
###  <a name="BKMK_EnumerationEdits"></a> Modifications relatives aux énumérations  
 Les modifications apportées aux énumérations (`Enums`) ne sont pas autorisées par Modifier & Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Modification du type sous-jacent d'un `Enum`.  
  
-   Ajout, changement ou suppression d'un membre `Enum`.  
  
-   Modification du modificateur d’accès d’un `Enum`.  
  
###  <a name="BKMK_ExternalDeclarationsEdits"></a> Modifications relatives aux déclarations externes  
 En général, vous ne pouvez pas modifier les déclarations de méthodes externes pendant Modifier & Continuer. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Ajout ou suppression d'une déclaration externe.  
  
-   Modification de la signature ou des attributs de marshaling d’une déclaration externe.  
  
###  <a name="BKMK_ImportsEdits"></a> Modifications relatives aux importations  
 Modifier & Continuer n'autorise pas l'ajout, le changement ou la suppression d'instructions `Imports` en mode Arrêt.  
  
###  <a name="BKMK_InterfaceDefinitionEdits"></a> Modifications de la définition d’interface  
 Bien que vous soyez fréquemment autorisés à apporter des modifications aux membres qui implémentent des interfaces, les modifications aux définitions d'interface ne sont pas autorisées en général par Modifier et Continuer. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Ajout, modification ou suppression de membres d'interface.  
  
-   Suppression d'une interface existante.  
  
-   Modification du modificateur d’accès d’une interface.  
  
-   Modification de la hiérarchie d'héritage de l'interface.  
  
###  <a name="BKMK_ModuleDeclarationEdits"></a> Modifications relatives aux déclarations de module  
 La plupart des modifications aux déclarations de module ne sont pas autorisées par Modifier & Continuer en mode Arrêt. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Création d'un nouveau module.  
  
-   Attribution d'un nouveau nom ou suppression d'un module existant.  
  
-   Modification du modificateur d’accès d’un module.  
  
###  <a name="BKMK_ModuleMemberDeclarationEdits"></a> Modifications de déclaration de membre de module  
 À l'aide de Modifier & Continuer, vous pouvez apporter différentes modifications aux membres de module, tels que propriétés, méthodes et champs, en mode Arrêt. Certaines modifications ne sont toutefois pas prises en charge. Plus particulièrement, Modifier & Continuer ne prend pas en charge l'ajout, la suppression ni la modification du type ou de la signature de membres quelconques.  
  
 En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Ajout d'un nouveau membre à moins qu'il n'existe pas d'occurrence de ce nom dans une quelconque instruction active.  
  
-   Suppression d'une propriété ou méthode.  
  
-   Modification de la signature d'une propriété ou d'une méthode.  
  
-   Ajout, modification du nom, déplacement ou suppression d'un champ.  
  
-   Modification de toute méthode qui utilise des génériques.  
  
-   Modification des modificateurs d'accès d'une propriété ou d'une méthode, par exemple, remplacer `Public` par `Private`.  
  
-   Suppression ou modification du type d'un champ existant.  
  
###  <a name="BKMK_NestedTypeDeclarationEdits"></a> Modifications relatives aux déclarations de Type imbriqué  
 Modifier & Continuer ne prend pas en charge le déplacement d'un type imbriqué vers un autre espace de noms ou type.  
  
###  <a name="BKMK_StructureDeclarationEdits"></a> Modifications relatives aux déclarations de structure  
 La plupart des modifications aux déclarations de structure ne sont pas autorisées par Modifier & Continuer en **rompre** mode. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Attribution d'un nouveau nom ou suppression d'une structure existante.  
  
-   Implémentation d'une nouvelle interface ou suppression de l'implémentation d'une interface.  
  
-   Modification du modificateur d’accès d’une structure.  
  
###  <a name="BKMK_StructureMemberDeclarationEdits"></a> Modifications de déclaration de membre de structure  
 À l'aide de Modifier & Continuer, vous pouvez apporter différentes modifications aux membres de structure (propriétés, méthodes et champs) en mode Arrêt. Toutefois, certaines modifications ne sont pas prises en charge, en particulier celles qui affectent la déclaration de membres de structure. En particulier, la fonctionnalité Modifier & Continuer ne prend pas en charge les modifications suivantes :  
  
-   Suppression d'une propriété ou méthode.  
  
-   Ajout ou suppression d'un champ.  
  
-   Modification de la signature d'une propriété ou d'une méthode.  
  
-   Modification de toute méthode qui utilise des génériques.  
  
-   Sélection d'une déclaration de propriété ou de méthode pour implémenter une interface.  
  
-   Modification des modificateurs d’accès d’une propriété ou une méthode (par exemple, la modification `Public` à **privé**).  
  
-   Suppression d'un champ.  
  
-   Modification d'un type de champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : appliquer des modifications en Mode arrêt avec Modifier & Continuer](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Modifier & Continuer (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



