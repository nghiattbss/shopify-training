# Shopify React Hook
Được extend từ [React-Hook-Form](https://react-hook-form.com/).

Chi tiết hướng dẫn sử dụng [tại đây](https://www.npmjs.com/package/@shopify/react-form).

### Chú ý:
- Shopify React Form (SRF) hoạt động tốt nhất với Shopify Polaris
- Có thể sử dụng để quản lý các form không quá phức tạp
- Khi có nhiều child component trong form, không nên sử dụng SRF, mà nên sử dụng phương pháp hoặc redux để quản lý trạng thái
- Một số component SRF vẫn chưa hỗ trợ ví dụ:
  - asChoiceList(): chỉ hoạt động với  radio button groups, not checkbox groups; allowMultiple sẽ luôn được sét là False.
- Trong bài tập phần này, cố gắng sử dụng SRF khi có thể.
### Code Example

```
import React from 'react';
import {useField, useForm, notEmpty, lengthMoreThan} from '@shopify/react-form';

import {
  Page,
  Layout,
  FormLayout,
  Form,
  Card,
  TextField,
  ContextualSaveBar,
  Frame,
  Banner,
} from '@shopify/polaris';

export default function MyComponent() {
  const {fields, submit, submitting, dirty, reset, submitErrors, makeClean} =
    useForm({
      fields: {
        title: useField({
          value: '',
          validates: [
            notEmpty('Title is required'),
            lengthMoreThan(3, 'Title must be more than 3 characters'),
          ],
        }),
        description: useField(''),
      },
      async onSubmit(form) {
        const remoteErrors = []; // your API call goes here
        if (remoteErrors.length > 0) {
          return {status: 'fail', errors: remoteErrors};
        }

        return {status: 'success'};
      },
    });

  const contextBar = dirty ? (
    <ContextualSaveBar
      message="Unsaved product"
      saveAction={{
        onAction: submit,
        loading: submitting,
        disabled: false,
      }}
      discardAction={{
        onAction: reset,
      }}
    />
  ) : null;

  const errorBanner =
    submitErrors.length > 0 ? (
      <Layout.Section>
        <Banner status="critical">
          <p>There were some issues with your form submission:</p>
          <ul>
            {submitErrors.map(({message}, index) => {
              return <li key={`${message}${index}`}>{message}</li>;
            })}
          </ul>
        </Banner>
      </Layout.Section>
    ) : null;

  return (
    <Frame>
      <Form onSubmit={submit}>
        <Page title="New Product">
          {contextBar}
          <Layout>
            {errorBanner}
            <Layout.Section>
              <Card sectioned>
                <FormLayout>
                  <TextField label="Title" {...fields.title} />
                  <TextField
                    multiline
                    label="Description"
                    {...fields.description}
                  />
                </FormLayout>
              </Card>
            </Layout.Section>
          </Layout>
        </Page>
      </Form>
    </Frame>
  );
}
```