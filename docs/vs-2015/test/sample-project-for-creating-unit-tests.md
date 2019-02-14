---
title: Exemple de projet pour la création de tests unitaires | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c2516a204151267f6d4686811fe6a7ecba5fe43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791894"
---
# <a name="sample-project-for-creating-unit-tests"></a>Exemple de projet pour la création de tests unitaires
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cet exemple de code est fourni pour une utilisation dans les procédures suivantes :  
  
-   [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Cette procédure pas à pas vous guide à travers les étapes de création et de personnalisation des tests unitaires, de leur exécution et de l'examen des résultats des tests.  
  
-   [Procédure pas à pas : Exécuter des tests et afficher la couverture du code](http://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). Cette procédure pas à pas illustre comment afficher les données de couverture du code, qui affiche la proportion du code de votre projet en cours de test.  
  
-   [Procédure pas à pas : utilisation de l’utilitaire de test de ligne de commande](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). Dans cette procédure pas à pas, vous utilisez l'utilitaire en ligne de commande MSTest.exe pour exécuter les tests et afficher les résultats.  
  
## <a name="sample-code"></a>Exemple de code  
 L'unique erreur intentionnelle de cet exemple est que dans la méthode Debit « m_balance += amount » doit avoir le signe moins (-) et non le signe plus (+) devant le signe égal.  
  
```  
using System;   
  
namespace BankAccountNS  
{  
    /// <summary>   
    /// Bank Account demo class.   
    /// </summary>   
    public class BankAccount  
    {  
        private string m_customerName;  
  
        private double m_balance;  
  
        private bool m_frozen = false;  
  
        private BankAccount()  
        {  
        }  
  
        public BankAccount(string customerName, double balance)  
        {  
            m_customerName = customerName;  
            m_balance = balance;  
        }  
  
        public string CustomerName  
        {  
            get { return m_customerName; }  
        }  
  
        public double Balance  
        {  
            get { return m_balance; }  
        }  
  
        public void Debit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount > m_balance)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount; // intentionally incorrect code  
        }  
  
        public void Credit(double amount)  
        {  
            if (m_frozen)  
            {  
                throw new Exception("Account frozen");  
            }  
  
            if (amount < 0)  
            {  
                throw new ArgumentOutOfRangeException("amount");  
            }  
  
            m_balance += amount;  
        }  
  
        private void FreezeAccount()  
        {  
            m_frozen = true;  
        }  
  
        private void UnfreezeAccount()  
        {  
            m_frozen = false;  
        }  
  
        public static void Main()  
        {  
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);   
  
            ba.Credit(5.77);  
            ba.Debit(11.22);  
            Console.WriteLine("Current balance is ${0}", ba.Balance);  
        }  
  
    }  
}  
```  
  
 /* Les noms de sociétés, d'organisations, de produits, de domaines, d'adresses de messagerie, de logos, de personnes, de lieux et d'événements mentionnés dans les exemples sont fictifs.  Toute ressemblance avec des noms ou des événements réels est purement fortuite et involontaire. \*/  
  
## <a name="working-with-the-code"></a>Utilisation du code  
 Pour utiliser ce code, vous devez d'abord créer un projet pour lui dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Suivez les étapes décrites dans la section « Préparer la procédure pas à pas » dans [procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création et exécution de tests unitaires pour le code managé](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Procédure pas à pas : Exécuter des tests et afficher la couverture du code](http://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Procédure pas à pas : utilisation de l’utilitaire de test de ligne de commande](http://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
