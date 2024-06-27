<template>
    <div class="card-front">
        <div class="center-wrap">
            <Form @submit="login" class="section text-center" :validation-schema="loginFromSchema">
                <h4 class="mb-4 pb-3">ورود</h4>
				<div class="form-group">
					<Field type="text" class="form-style" placeholder="ایمیل خود را وارد کنید" autocomplete="off" name="email" validate-on-input="true"/>
                    <i class="input-icon uil uil-at"></i>
                    <p class="text-danger">
                        <ErrorMessage name="email"/>
                    </p>
				</div>	
				<div class="form-group mt-2">
					<Field type="password" class="form-style" placeholder="پسورد خود را وارد کنید" autocomplete="off" name="password"  validate-on-input="true" />
					<i class="input-icon uil uil-lock-alt"></i>
                    <p class="text-danger">
                        <ErrorMessage name="password"/>
                    </p>
				</div>
				<button class="btn mt-4">تایید</button>
                <p class="mb-0 mt-4 text-center"><a href="#0" class="link">فراموشی رمز عبور</a></p>
            </Form>
        </div>
    </div>
</template>

<script>
import {Form, Field, ErrorMessage} from 'vee-validate';
import {string, object} from 'yup';
export default{
    components :{
        Form,
        Field,
        ErrorMessage
    },
    data(){
        const loginFromSchema = object({
            email: string().required("ایمیل را وارد کنید").email("ایمیل نا متعبراست"),
            password: string().required("کلمه عبور مورد نیازاست").min(6, "کلمه عبور باید بیشتر از 5 کاراکتر باشد"),
        })
        return{
            loginFromSchema,
        };
    },
    methods : {
        login(values){
            console.log(values);
        },
    },
}
</script>

<style>
</style>
