# **Síntese dos Componentes de Arquitetura do Microsoft Azure (AZ-900)**

Esta síntese aborda os principais pilares geográficos e de gerenciamento que compõem a arquitetura fundamental do Microsoft Azure.

## **1\. Estrutura Geográfica e de Continuidade**

A arquitetura do Azure é projetada para ser global, resiliente e focada na conformidade, com base nos seguintes componentes:

* **Regiões:** Uma região é uma área geográfica que contém um ou mais **Datacenters** próximos, interconectados por uma rede de fibra óptica dedicada e de alta velocidade. O Azure possui a maior cobertura global de qualquer provedor de nuvem, o que garante baixa latência e permite aos clientes cumprir requisitos de residência de dados e conformidade local.  
* **Zonas de Disponibilidade (Availability Zones):** São locais física e logicamente separados dentro de uma Região do Azure. Cada Zona de Disponibilidade possui energia, resfriamento e rede independentes. Elas fornecem proteção contra falhas locais (como falha de hardware ou interrupção de energia em um datacenter) e são a base para construir aplicações de alta disponibilidade.  
* **Pares de Regiões (Region Pairs):** Duas regiões dentro da mesma área geográfica são emparelhadas, geralmente separadas por pelo menos 300 milhas. Esse emparelhamento é vital para a Recuperação de Desastres (DR) e atualizações de plataforma:  
  * A replicação de dados em alguns serviços de armazenamento ocorre automaticamente e de forma assíncrona para o par.  
  * O Azure prioriza a recuperação de uma região de cada par de regiões em caso de desastre, garantindo que pelo menos um dos pares seja restaurado rapidamente.  
  * Atualizações e manutenções de plataforma são distribuídas sequencialmente para os pares, minimizando o tempo de inatividade.  
* **Regiões Soberanas:** Instâncias isoladas do Azure (como o Azure Governamental) que atendem a necessidades específicas de segurança e conformidade de agências governamentais e seus provedores de soluções. Essas instâncias são fisicamente isoladas da nuvem pública e acessíveis apenas a pessoal verificado e autorizado.

## **2\. Estrutura de Gerenciamento e Governança**

O Azure utiliza um sistema hierárquico para organizar, gerenciar e aplicar políticas aos recursos implantados.

* **Recursos do Azure:** São os itens concretos que você cria e usa, como Máquinas Virtuais (VMs), Contas de Armazenamento, Bancos de Dados SQL, Redes Virtuais e Azure Functions.  
* **Grupos de Recursos (Resource Groups \- RGs):** Um contêiner lógico que você usa para agrupar recursos relacionados a uma aplicação ou solução.  
  * Um recurso só pode pertencer a um único RG por vez.  
  * Recursos em um RG podem ser movidos e podem estar em diferentes regiões geográficas.  
  * O RG é o escopo onde o gerenciamento de ciclo de vida (implantação, atualização e exclusão) e o controle de acesso são frequentemente aplicados.  
* **Assinaturas (Subscriptions):** O limite primário para acesso, cobrança e limites de serviço. Uma assinatura:  
  * Fornece acesso autenticado e autorizado à sua conta do Azure.  
  * Serve como limite de **Cobrança**, permitindo gerar faturas separadas (por exemplo, para diferentes departamentos).  
  * Serve como limite de **Controle de Acesso**, gerenciando quais usuários podem provisionar e usar recursos.  
* **Grupos de Gerenciamento (Management Groups):** O nível mais alto na hierarquia de governança. Eles permitem agrupar várias Assinaturas do Azure em uma única estrutura. As políticas e o controle de acesso aplicados a um Grupo de Gerenciamento são herdados por todas as assinaturas e grupos de recursos aninhados. Isso é fundamental para a governança em grande escala.

## **Hierarquia de Gerenciamento do Azure**

Os componentes de gerenciamento formam uma hierarquia clara que garante a governança e o controle de cima para baixo:

$$\\text{Grupos de Gerenciamento} \\rightarrow \\text{Assinaturas} \\rightarrow \\text{Grupos de Recursos} \\rightarrow \\text{Recursos}$$

## **Contas do Azure**

Para começar a usar os serviços, é necessário uma Conta do Azure. As opções incluem a Conta do Azure padrão (paga), a Conta Gratuita (com créditos iniciais e serviços grátis por 12 meses) e a Conta de Estudante Gratuita.