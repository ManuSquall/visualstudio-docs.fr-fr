---
title: "CA2210 : Les assemblys doivent avoir des noms forts valides | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 066c78158b688db8164a5ebf23dbe957c7c324ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210 : Les assemblys doivent porter des noms forts valides
|||  
|-|-|  
|TypeName|AssembliesShouldHaveValidStrongNames|  
|CheckId|CA2210|  
|Category|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un assembly n’est pas signé avec un nom fort, le nom fort n’a pas pu être vérifié ou le nom fort ne serait pas valide sans les paramètres de Registre actuels de l’ordinateur.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle récupère et vérifie le nom fort d’un assembly. Une violation se produit si une des conditions suivantes est vraie :  
  
-   L’assembly n’a pas un nom fort.  
  
-   L’assembly a été modifié après la signature.  
  
-   L’assembly est différée.  
  
-   L’assembly a été signé correctement ou la signature a échoué.  
  
-   L’assembly requiert des paramètres du Registre passer la vérification. Par exemple, l’outil Strong Name tool (Sn.exe) a été utilisé pour ignorer la vérification de l’assembly.  
  
 Le nom fort protège les clients du chargement à leur insu d'un assembly falsifié. Les assemblys sans noms forts ne doivent pas être déployés hors de scénarios très limités. Si vous partagez ou distribuez des assemblys qui ne sont pas signés correctement, ceux-ci peuvent être falsifiés, le Common Language Runtime peut ne pas les charger ou l'utilisateur peut être amené à désactiver une vérification sur son ordinateur. Un assembly sans nom fort présente les inconvénients suivants :  
  
-   Impossible de vérifier son origine.  
  
-   Le common language runtime ne peut pas avertir les utilisateurs si le contenu de l’assembly a été modifié.  
  
-   Il ne peut pas être chargé dans le global assembly cache.  
  
 Notez que pour charger et analyser un assembly à signature différée, vous devez désactiver la vérification de l’assembly.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 **Pour créer un fichier de clé**  
  
 Utilisez une des procédures suivantes :  
  
-   Utilisez l’outil Assembly Linker (Al.exe) fourni par le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Kit de développement logiciel.  
  
-   Pour le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] v1.0 ou v1.1, utilisez le <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> ou <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> attribut.  
  
-   Pour le [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], soit utiliser le `/keyfile` ou `/keycontainer` option du compilateur [/KEYFILE (spécifier la clé ou la paire de clés pour signer un Assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) ou [/KEYCONTAINER (spécifier un conteneur de clé pour signer un Assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) option de l’éditeur de liens c++).  
  
 **Pour signer votre assembly avec un nom fort dans Visual Studio**  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez votre solution.  
  
2.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis sur **propriétés.**  
  
3.  Cliquez sur le **signature** et sélectionnez le **signer l’assembly** case à cocher.  
  
4.  À partir de **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.  
  
     Le **créer une clé de nom fort** fenêtre s’affiche.  
  
5.  Dans **nom de fichier de clé**, tapez un nom pour votre clé de nom fort.  
  
6.  Choisissez si vous souhaitez protéger la clé avec un mot de passe, puis cliquez sur **OK**.  
  
7.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis sur **Build**.  
  
 **Pour signer votre assembly avec un nom fort en dehors de Visual Studio**  
  
-   Utilisez l’outil strong name (Sn.exe) fourni par le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Kit de développement logiciel. Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimez uniquement un avertissement de cette règle si l’assembly est utilisé dans un environnement où falsifier le contenu n’est pas un problème.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [Guide pratique pour signer un assembly avec un nom fort](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)   
 [Sn.exe (outil Strong Name)](/dotnet/framework/tools/sn-exe-strong-name-tool)