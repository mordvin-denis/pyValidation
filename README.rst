pyValidation: simple module for validation without any framework
=========================

Using example:

.. code-block:: python

    def validate_search_params(params):
        validate(u'Откуда', params['departureFrom'], required, regex(ur'^[A-ZА-ЯЁ]{3}$'))
        validate(u'Куда', params['arrivalTo'], required, regex(ur'^[A-ZА-ЯЁ]{3}$'))
        validate(u'Туда', params['date'], required, date_string('%Y-%m-%dT%H:%M:%S'))
        validate(u'Класс', params['sclass'], required, value_in(CLASS_TYPES.values()))
        validate(u'Количество взрослых', params['adults'], required, value_in(range(1, 7)))

    # In view
        try:
            validate_search_params(params)
        except FieldValidationError as ex:
            #
    ...
