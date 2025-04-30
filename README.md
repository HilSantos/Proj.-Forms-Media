# Proj.-Forms-Media
CRIE UM PROJETO WINDOWS FORMS CHAMADO "PROJETOFORMSMEDIA" E TENHA 4 TEXTBOX´S PARA RECEBER AS NOTAS PARA O CÁLCULO DA MÉDIA ARITMÉTICA: -NOTA 1 (TXTNOTA1) -NOTA 2 (TXTNOTA2) -NOTA 3 (TXTNOTA3) -NOTA 4 (TXTNOTA4). COLOQUEM AS LABEL´S PARA ROTULAR OS CAMPOS COM 2 BOTÕES: MÉDIA(BTNMEDIA) E LIMPAR(BTNLIMPAR). AO CLICAR NO BTNMEDIA, DEVERÁ PRIMEIRO VERIFICAR SE OS TEXTBOX´S ESTÃO PREENCHIDOS COM VALORES NUMÉRICOS, CASO CONTRÁRIO EXIBIR UMA MSG EM UMA LABEL(LBLSTATUS), CASO ESTEJAM PREENCHIDOS CAPTURAR OS VALORES DOS TEXTBOX´S E EFETUAR A OPERAÇÃO E PASSAR PELA SEGUINTE ANÁLISE:
-SE MÉDIA >=7 (SITUAÇÃO APROVADO)
-SE MÉDIA >=5 E MÉDIA <7 (SITUAÇÃO RECUPERAÇÃO)
-SE MÉDIA <5 (SITUAÇÃO REPROVADO)
EXIBIR O VALOR DA MÉDIA E A SITUAÇÃO EM UMA LABEL(LBLRESULTADO).
-----------------------------------------------------------------------------------------------------------------------------------

Crie um novo projeto do tipo Windows Forms App (.NET Framework) chamado ProjetoFormsMedia.

No formulário (Form1), adicione:

4 TextBoxes com os nomes:

txtNota1

txtNota2

txtNota3

txtNota4

4 Labels para identificar cada nota (ex: "Nota 1:", etc.).

2 Botões:

btnMedia com texto "Média"

btnLimpar com texto "Limpar"

2 Labels:

lblResultado → para exibir a média e situação

lblStatus → para exibir mensagens de erro
------------------------------------------------------------------------------------------------------------------------------------

using System;
using System.Windows.Forms;

namespace ProjetoFormsMedia
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

  private void btnMedia_Click(object sender, EventArgs e)
        {
            lblStatus.Text = "";
            lblResultado.Text = "";

  double nota1, nota2, nota3, nota4;

  bool valido = double.TryParse(txtNota1.Text, out nota1)
                       && double.TryParse(txtNota2.Text, out nota2)
                       && double.TryParse(txtNota3.Text, out nota3)
                       && double.TryParse(txtNota4.Text, out nota4);

  if (!valido)
            {
                lblStatus.Text = "Preencha todos os campos com valores numéricos válidos.";
                return;
            }

  double media = (nota1 + nota2 + nota3 + nota4) / 4;
            string situacao;

  if (media >= 7)
                situacao = "Aprovado";
            else if (media >= 5)
                situacao = "Recuperação";
            else
                situacao = "Reprovado";

  lblResultado.Text = $"Média: {media:F2} - Situação: {situacao}";
        }

  private void btnLimpar_Click(object sender, EventArgs e)
        {
            txtNota1.Clear();
            txtNota2.Clear();
            txtNota3.Clear();
            txtNota4.Clear();
            lblResultado.Text = "";
            lblStatus.Text = "";
            txtNota1.Focus();
        }
    }
}

