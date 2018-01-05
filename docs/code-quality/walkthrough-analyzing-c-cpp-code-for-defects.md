---
title: "Procédure pas à pas : Analyse du Code C/C++ pour les erreurs de | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c95d03201fe9c84e01e83e7fd55bef83755337e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procédure pas à pas : analyse du code C/C++ pour rechercher les erreurs
Cette procédure pas à pas montre comment analyser du code C/C++ pour les erreurs potentielles de code à l’aide de l’outil d’analyse du code pour le code C/C++.  
  
 Dans cette procédure pas à pas, vous parcourez le processus de l’utilisation de l’analyse du code pour analyser votre code C/C++ pour les erreurs potentielles.  
  
 Vous allez effectuer les étapes suivantes :  
  
-   Exécuter l’analyse du code sur le code natif.  
  
-   Analyser les avertissements d’erreur de code.  
  
-   Traiter l’avertissement comme une erreur.  
  
-   Annoter le code source pour améliorer l’analyse des erreurs de code.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] ou [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Une copie de la [exemple de démonstration](../code-quality/demo-sample.md).  
  
-   Compréhension de base de C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Pour exécuter l’analyse des erreurs de code sur le code natif  
  
1.  Ouvrez la solution de démonstration dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     À présent dans la solution de démonstration **l’Explorateur de solutions**.  
  
2.  Sur le **générer** menu, cliquez sur **régénérer la Solution**.  
  
     La solution se génère sans aucun avertissement ni erreur.  
  
3.  Dans **l’Explorateur de solutions**, sélectionnez le projet CodeDefects.  
  
4.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     Le **les Pages de propriétés de CodeDefects** boîte de dialogue s’affiche.  
  
5.  Cliquez sur **l’analyse du Code**.  
  
6.  Cliquez sur le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.  
  
7.  Régénérez le projet CodeDefects.  
  
     Avertissements d’analyse du code sont affichent dans le **liste d’erreurs**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Pour analyser les avertissements d’erreur de code  
  
1.  Sur le **vue** menu, cliquez sur **liste d’erreurs**.  
  
     Selon le profil de développeur que vous avez choisi dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous devrez peut-être pointer vers **autres fenêtres** sur la **vue** menu, puis sur **liste d’erreurs**.  
  
2.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6230 : cast implicite entre types sémantiquement différents : utilisation de HRESULT dans un contexte Boolean.  
  
     L’éditeur de code affiche la ligne qui a provoqué l’avertissement dans la fonction `bool``ProcessDomain()`. Cet avertissement indique qu’une valeur HRESULT est utilisé dans une instruction 'if' où un résultat booléen est attendu.  
  
3.  Corriger cet avertissement à l’aide de la macro SUCCEEDED. Votre code doit ressembler au code suivant :  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6282 : opérateur Incorrect : attribution de constante dans un contexte de test. == Est-il intentionnel ?  
  
5.  Corriger cet avertissement en testant l’égalité. Votre code doit ressembler au code suivant :  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Pour traiter un avertissement comme une erreur  
  
1.  Dans le fichier Bug.cpp, ajoutez le code suivant `#pragma` instruction au début du fichier à traiter l’avertissement C6001 comme une erreur :  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Régénérez le projet CodeDefects.  
  
     Dans le **liste d’erreurs**, C6001 apparaît maintenant comme une erreur.  
  
3.  Corrigez les deux erreurs C6001 restantes dans le **liste d’erreurs** en initialisant `i` et `j` à 0.  
  
4.  Régénérez le projet CodeDefects.  
  
     Le projet se génère sans les avertissements ou erreurs.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Pour corriger les avertissements d’annotation de code source dans annotation.c  
  
1.  Dans l’Explorateur de solutions, sélectionnez le projet Annotations.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
     Le **les Pages de propriétés de Annotations** boîte de dialogue s’affiche.  
  
3.  Cliquez sur **l’analyse du Code**.  
  
4.  Sélectionnez le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher.  
  
5.  Régénérez le projet Annotations.  
  
6.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6011 : déréférencement du pointeur NULL 'newNode'.  
  
     Cet avertissement indique que l’appelant pour vérifier la valeur de retour. Dans ce cas, un appel à **AllocateNode** peut retourner une valeur NULL (voir le fichier d’en-tête annotations.h la déclaration de fonction d’AllocateNode).  
  
7.  Ouvrez le fichier annotations.cpp.  
  
8.  Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Régénérez le projet Annotations.  
  
     Le projet se génère sans les avertissements ou erreurs.  
  
### <a name="to-use-source-code-annotation"></a>Pour utiliser l’annotation de code source  
  
1.  Annotez les paramètres formels et la valeur de retour de la fonction `AddTail` en utilisant les conditions Pre et Post comme indiqué dans cet exemple :  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Régénérez le projet Annotations.  
  
3.  Dans le **liste d’erreurs**, double-cliquez sur l’avertissement suivant :  
  
     avertissement C6011 : suppression de référence un pointeur NULL 'nœud'.  
  
     Cet avertissement indique que le nœud passé dans la fonction peut être null et indique le numéro de ligne où l’avertissement a été déclenché.  
  
4.  Pour corriger cet avertissement, utilisez une instruction 'if' pour tester la valeur de retour. Votre code doit ressembler au code suivant :  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Régénérez le projet Annotations.  
  
     Le projet se génère sans les avertissements ou erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : analyse du code managé pour les erreurs de code](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)