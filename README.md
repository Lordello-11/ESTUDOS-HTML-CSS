import flet 
from flet import Text, TextField, FilledButton, Row, Banner, colors, Icon , icons, TextButton


def main(page):
    dict_values = {
        'contratante' : '',
        'medida_jidicial' : '',
        'outra_parte' : '',
        'prolabore' : '',
        'exito' : '',
        'foro' : '',
        'data' : '',
    }

    def gera_contrato(e):

        dict_values['contratante'] = contratante.value
        dict_values['medida_judicial'] = medida_jidicial.value
        dict_values['outra_parte'] =outra_parte .value
        dict_values['prolabore'] = prolabore.value
        dict_values['exito'] = exito.value
        dict_values['foro'] = foro.value
        dict_values['data'] = data.value

        for val in dict_values.values():
            if not val:
                page.banner.open=True
                page.update()
                return
            

        print('opa! já é possivel gerar o contrato.')

 

    def fecha_banner(e):
        page.banner.open=False
        page.update()



        
    page.banner = Banner(
        bgcolor=colors.BLACK,
        leading=Icon(
            icons.DANGEROUS_SHARP,
            color=colors.RED_400,
            size=40
            ),
        content=Text('todos os campos de preenchimento obrigatorio'),
        actions=[
            TextButton(
                'Entendi',
                on_click=fecha_banner
            )
        ]  
    )


        
    
    Titulo = Text(value='Gerador de contrato de prestação de serviço Advocaticios', size=20,weight='bold')
    contratante = TextField(label='Nome do contratante', autofocus=True)
    medida_jidicial = TextField(label='Medida Judicial')
    outra_parte = TextField(label='Outra parte')
    prolabore = TextField(label='Prolabore',prefix_text='R$ ')
    exito = TextField(label='Exito',suffix_text=' %')
    foro = TextField(label='Foro')
    data = TextField(label='Data do contrato')
    botao_gerar = FilledButton('Gerar Contrato', on_click=gera_contrato)

    page.add (
        Row (
            controls =[
                Titulo  
            ]
        ),
        Row(
            controls = [
                contratante
            ]
        ),
        Row(
            controls = [
                medida_jidicial,
                outra_parte
            ]
        ),
                Row(
            controls = [
                prolabore,
                exito
            ]
        ),
                Row(
            controls = [
                foro,
                data
            ]
        ),
        Row(
            controls = [
                botao_gerar
            ]
        ),
    )

flet.app(target=main)
