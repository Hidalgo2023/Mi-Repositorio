# Mi-Parcial 

def calcular_precio_boletas(num_boletas, tipo_sala, hora, medio_pago, reserva):
    tarifa = 0
    if tipo_sala == 'Dinamix':
        tarifa = 18800
    elif tipo_sala == '3D':
        tarifa = 15500
    elif tipo_sala == '2D':
        tarifa = 11300

    if hora < 16 or hora > 21:
        descuento_horas_no_pico = 0.1
        descuento_boletas_multiples = 0
        if num_boletas >= 3:
            descuento_boletas_multiples = 500
        descuento_promocion = (descuento_horas_no_pico * tarifa) + (descuento_boletas_multiples * (num_boletas - 1))
        tarifa = tarifa - descuento_promocion

    if medio_pago == 'tarjeta_cinema':
        descuento_tarjeta = 0.05 * tarifa
        tarifa = tarifa - descuento_tarjeta

    if reserva:
        recargo_reserva = 2000
        tarifa = tarifa + recargo_reserva

    if 16 <= hora <= 21:
        if tipo_sala == '2D' or tipo_sala == '3D':
            tarifa = tarifa * 1.25
        elif tipo_sala == 'Dinamix':
            tarifa = tarifa * 1.50

    precio_total = tarifa * num_boletas
    return precio_total
